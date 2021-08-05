---
title: Preguntas más frecuentes sobre la visualización de cascos
description: Mostrar Windows Mixed Reality solución de problemas de visualización de cascos que van más allá de la documentación de soporte técnico al consumidor estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support
appliesto:
- Windows 10
ms.openlocfilehash: 811b5160c739c8b19fde737e7a61bcef84e0cf60a87927adbe21241e229f3f22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189397"
---
# <a name="headset-display-faqs"></a>Preguntas más frecuentes sobre la pantalla del casco

## <a name="my-headset-displays-are-black"></a>Mis pantallas de casco son de color negro

* Compruebe el rendimiento y la estabilidad del equipo:
    * Use el Administrador de tareas para ver si algún proceso está maximizando la CPU, la GPU o las unidades de disco del equipo.
    * Compruebe los registros "Aplicación" y "Sistema" en Visor de eventos > Windows **Logs** para ver si una aplicación se bloquea y genera informes Informe de errores de Windows (WER).
    * Compruebe Windows update para asegurarse de que la versión de Windows está actualizada. Es posible que tenga que seleccionar "Buscar actualizaciones" varias veces.
* Comprobar la estabilidad de la aplicación y el juego:
    * Asegúrese de que el equipo cumple los requisitos mínimos del sistema de cualquier aplicación o juego que no se ejecute correctamente.
    * Asegúrese de que la versión del controlador de GPU es reciente y compruebe si hay nuevos problemas de rendimiento y compatibilidad y regresiones en los nuevos controladores.
    * Si usa aplicaciones y juegos de SteamVR, asegúrese de que Tanto SteamVR como los Windows Mixed Reality para los componentes de SteamVR estén actualizados.
* Compruebe la compatibilidad del adaptador de HDMI:
    * Asegúrese de que el cable HDMI está conectado todo el proceso.
    * Si usa un adaptador HDMI (por ejemplo, un adaptador Mini DisplayPort a HDMI), asegúrese de que es compatible con Windows Mixed Reality. El adaptador debe admitir HDMI 2.0 y hay muchos adaptadores más antiguos que solo admiten 1080p. Consulte [Adaptadores recomendados para Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * El pedido de conexión puede ser importante. Conectar el adaptador de HDMI al equipo antes de conectar el casco al adaptador, especialmente si usa un adaptador de USB-C a HDMI.
    * Intente quitar los cables de extensión si los usa.
* Compruebe la compatibilidad de tarjetas gráficas y controladores:
    * Pruebe el puerto HDMI del equipo con un monitor de equipo. Algunos equipos pueden tener más de un puerto HDMI y no todos ellos pueden estar activos.
    * Si el equipo tiene una unidad de procesamiento de gráficos integrada (iGPU) y una unidad de procesamiento de gráficos discreto (dGPU), asegúrese de que está conectado al puerto HDMI de dGPU.
    * Compruebe la versión del controlador de GPU. Asegúrese de que es reciente, pero también preste atención a los nuevos problemas de rendimiento y compatibilidad y regresiones en nuevos controladores.
    * Si usa Mixed Reality en un portátil y ha instalado un controlador de gráficos más reciente desde el sitio web del fabricante de tarjetas gráficas, pruebe a cambiar a la versión más reciente del controlador de tarjeta gráfica que se proporciona en el sitio web del fabricante del equipo o en Windows Update.
    * Si tiene varios monitores de pc conectados al equipo, intente desconectar temporalmente todos los monitores de pc, menos uno.
    * Si ha establecido una frecuencia de actualización personalizada para el monitor de pc, intente revertir temporalmente a una frecuencia de actualización estándar, como 60 Hz.
    * Si ha cambiado recientemente la tarjeta gráfica sin volver a Windows, compruebe que el monitor de cascos sigue teniendo instalado el controlador correcto. Con el casco conectado, confirme que "Mixed Reality casco" aparece en el nodo Monitores de Administrador de dispositivos.
    * Si el equipo tiene una tarjeta gráfica Nvidia, asegúrese de que el software 3D Vision de Nvidia está deshabilitado.
    * En algunas tarjetas gráficas (especialmente las tarjetas anteriores), es posible que el puerto HDMI no admita HDMI 2.0 o que no sea totalmente compatible con Windows Mixed Reality. Pruebe a usar displayport de la tarjeta gráfica con un [adaptador De DisplayPort 1.2 a HDMI 2.0.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
    * Los equipos de HP Omen con el número de producto HP 1RJ99EA#SVC tienen puertos HDMI incompatibles con Windows Mixed Reality (abra el "Asistente de soporte técnico de HP" y el número aparecerá en la parte inferior de la aplicación).
    * Si el equipo tiene una tarjeta gráfica de la serie AMD R9 y usa un casco Samsung Mixed Reality, actualice el firmware del casco a la versión 1.0.8 o posterior para usar el puerto HDMI de la tarjeta gráfica con el casco.
    * Si usa un Surface Book 2, asegúrese de que usa el adaptador [de Surface USB-C a HDMI.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Compruebe si hay un problema Mixed Reality hardware del casco:
    * Para confirmar o descartar problemas de hardware con el casco, conecte el casco Mixed Reality a otro equipo.
    * Compruebe primero si hay problemas de compatibilidad y configuración del equipo, ya que los síntomas son similares.
* Asegúrese de que el cable USB está conectado a un puerto USB 3.0 o más rápido. Los puertos USB 3.0 tienen SS (Super Speed) junto a ellos y a menudo tienen color azul.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>En ocasiones, la pantalla del casco se vuelve negra después de algún uso

* Pruebe a deshabilitar las características de suspensión o ahorro de energía USB en el equipo. Por ejemplo, en Configuración > **System > Power & Sleep > USB selective [suspend](/windows-hardware/drivers/usbcon/usb-selective-suspend)**, la opción "Permitir que el equipo apague este dispositivo para ahorrar energía" en Administrador de dispositivos y cualquier configuración de ahorro de energía USB en el firmware del equipo.
* Desconecte temporalmente cualquier otro dispositivo USB y periférico conectado al equipo.
* Compruebe que la versión del controlador de GPU es reciente y compruebe si hay nuevos problemas de rendimiento y compatibilidad y regresiones en los nuevos controladores.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Una de las pantallas del casco es negra

* Si usa un adaptador hdmi, asegúrese de que es compatible con HDMI 2.0.
* Quite los cables de extensión USB y HDMI que pueda usar.
* Asegúrese de que el controlador de gráficos está actual.
* Pruebe el casco Mixed Reality en otro equipo.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Mi casco se muestra en azul y, a continuación, Portal de realidad mixta reinicializa

Esto suele indicar un problema ocasional de confiabilidad del controlador USB en el equipo:

* Pruebe otro puerto USB. El equipo puede tener varios controladores USB 3.0.
* Quite los cables de extensión (si procede).
* Desconecte todos los demás dispositivos USB del equipo.
* Conectar un concentrador USB 3.0 con tecnología externa al equipo y conecte el casco al centro.
* Si usa un equipo de escritorio, considere la posibilidad de comprar una tarjeta PCIe USB 3.0 para agregar otro controlador USB al equipo.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>El casco hace que mi PC se queme o muestre una pantalla negra durante el inicio

En algunos equipos, dejar el casco conectado antes de encender o al reiniciar el equipo puede interferir con su proceso de inicio. El equipo podría seleccionar las pantallas de casco como el "monitor principal" para mostrar el progreso de inicio del equipo, no iniciarse correctamente, o "parar" o generar un código de error de pitido. El comportamiento depende de la realización y el modelo del equipo o de la imagen y el modelo de la tarjeta gráfica. Para solucionar este error:

* Conectar el casco a otro puerto de la tarjeta gráfica (es posible que tenga que usar un adaptador para usar los demás puertos).
* Asegúrese de que el firmware DE BIOS o UEFI del equipo esté actualizado (pero solo actualice el firmware DE BIOS o UEFI del equipo si se siente cómodo al hacerlo).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Mi PC o casco muestra parpadeo, flash o permanece negro cuando se usa un equipo Surface

* Asegúrese de que usa un adaptador hdmi compatible con HDMI 2.0. Muchos adaptadores HDMI más antiguos solo admiten una resolución de 1080p, lo que no es suficiente para Mixed Reality cascos.
* Asegúrese de que el controlador de gráficos está actualizado. Compruebe Windows actualización y el sitio web del fabricante del equipo para ver un controlador de gráficos actualizado.
* Algunos dispositivos Surface no son compatibles con Windows Mixed Reality. Obtenga más información sobre la [compatibilidad y los requisitos de Surface.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La pantalla del casco no funciona después de apagar y realizar un inicio rápido

Desconecte el cable HDMI y el cable USB del casco y vuelva a conectarlos.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Las pantallas de los cascos están abolladas, Portal de realidad mixta la ventana de vista previa parece estar bien.

* Asegúrese de que los recursos del sistema del equipo (CPU, memoria y unidad de disco duro) están disponibles y no los consume otra aplicación o proceso.
* Actualice el controlador de gráficos.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Aparece el error "La clase de instalación no está presente o no es válida" en Administrador de dispositivos

Si ve "sensores de HoloLens" con un signo de exclamación amarillo en Administrador de dispositivos, seleccione el dispositivo para obtener más detalles. Si ve un mensaje que dice "Los controladores de este dispositivo no están instalados. (Código 28): la clase de instalación no está presente o no es válida", normalmente porque el equipo se [ejecuta Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). N ediciones de Windows 10 no admiten Windows Mixed Reality y deberá instalar una versión que no sea N de Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Mi entorno WMR está vibración o atascada cuando mudo la cabeza y muestra doble visión.

En un portátil con gráficos integrados y una GPU nvidia, se produce un error después de un período de tiempo que parece hacer que un fotograma anterior se muestre después del fotograma siguiente, lo que da lugar a una visión doble cuanto más rápido mueva la cabeza en un movimiento de guión, inclinación o desplazamiento. El problema parece estar en los controladores después de Nvidia Graphics Driver 436.48.  La instalación de este controlador corregirá el problema hasta que Nvidia resuelva el problema en los controladores actualizados. Para una instalación directa de Nvidia Graphics Driver 436.48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>No tengo incomodidad en los cascos

Para obtener información general sobre la comodidad Windows Mixed Reality, consulte Windows Mixed Reality de casco [envolvente, seguridad y confort.](wmr-health-safety-comfort.md) Para más información sobre el casco específico, consulte con el fabricante del casco.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>¿Cómo puedo obtener una vista más clara en el casco?

Intente ajustar el ajuste del casco. Muévelo hacia arriba y hacia abajo, o a la izquierda y derecha, en la cara y ajusta las cintas para que se sienta ajustado.

Si el casco tiene un mando para ajustar la calibración, ajuste su configuración de calibración. Si no es así, vaya a Configuración > **Mixed reality > Visual quality** (Calidad visual) y ajuste la calibración allí. Para obtener más información sobre la calibración del dispositivo específico, consulte con el fabricante del casco.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Con frecuencia veo un borde negro alrededor de la vista en el casco. A veces es como si mirara un túnel.

Esto significa que la aplicación no puede alcanzar la velocidad de fotogramas en el equipo y el sistema usa marcos antiguos para representar la vista en el casco. Dado que las aplicaciones solo representan la parte del mundo que está viendo, si no se alcanzaron sistemáticamente sus velocidades de fotogramas, el sistema intentará representar el mundo desde un punto de vista anterior y rellenará los detalles que faltan con negro. Si esto sucede con frecuencia:

1. Cierre o detenga todos los programas innecesarios para liberar memoria y CPU.
2. Reduzca la configuración de detalles en la aplicación.
3. Vaya a **Configuración > Mixed Reality > Headset Display** para reducir la cantidad de detalles que se muestra en Windows Mixed Reality inicio.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La vista en el casco se está quemándose y ateando mucho.

Es posible que el sistema no pueda representar contenido en el casco o que el sistema de seguimiento esté experimentando problemas:

1. Abra Administrador de tareas asegurarse de que el equipo tiene suficientes recursos de proceso. Debe tener un 80 % de CPU libre, 400 MB de RAM y la E/S de disco debe estar por debajo del 80 %.
2. Asegúrese de que tiene los controladores de gráficos más recientes para el hardware. Consulte la sección [controlador de gráficos](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Asegúrese de que la sala tiene suficiente luz.
4. Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectarlo.
5. Reinicia tu equipo.
6. Si el problema persiste, póngase en contacto con el [servicio de soporte al cliente.](https://support.microsoft.com/)