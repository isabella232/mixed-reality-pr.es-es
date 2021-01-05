---
title: Preguntas más frecuentes sobre pantalla
description: Mostrar la solución de problemas de realidad mixta de Windows para la visualización de auriculares que va más allá de nuestra documentación de soporte técnico estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico
appliesto:
- Windows 10
ms.openlocfilehash: 6bcd6db30bf3a8a6e69d45c10be523d45ee4f82a
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725416"
---
# <a name="headset-display-faqs"></a>Preguntas más frecuentes sobre pantalla

## <a name="my-headset-displays-are-black"></a>Los auriculares aparecen en negro

* Compruebe el rendimiento y la estabilidad del equipo:
    * Use el administrador de tareas para ver si se agotan los procesos de la CPU, la GPU o las unidades de disco del equipo.
    * Compruebe los registros "aplicación" y "sistema" en **Visor de eventos > registros de Windows** para ver si una aplicación se bloquea y genera informes informe de errores de Windows (WER).
    * Compruebe Windows Update para asegurarse de que la versión de Windows sea la actual. Es posible que tenga que seleccionar varias veces "buscar actualizaciones".
* Comprobar la estabilidad de la aplicación y el juego:
    * Asegúrese de que su equipo cumple los requisitos mínimos del sistema de cualquier aplicación o juego que no se ejecuta correctamente.
    * Asegúrese de que la versión del controlador de GPU es reciente y compruebe si hay nuevos problemas de rendimiento y compatibilidad y regresiones en los controladores nuevos.
    * Si usa aplicaciones y juegos de SteamVR, asegúrese de que los componentes de SteamVR y Windows Mixed Reality para SteamVR están actualizados.
* Comprobar la compatibilidad del adaptador de HDMI:
    * Asegúrese de que el cable HDMI está enchufado.
    * Si usa un adaptador HDMI (por ejemplo, un adaptador de DisplayPort a HDMI), asegúrese de que es compatible con Windows Mixed Reality. El adaptador debe ser compatible con HDMI 2,0 y hay muchos adaptadores más antiguos que solo admiten 1080p. Consulte [adaptadores recomendados para Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * El orden de los conectores puede ser importante. Conecte el adaptador de HDMI al equipo antes de conectar los auriculares al adaptador, especialmente si usa un adaptador de USB a HDMI.
    * Intente quitar los cables de extensión si los está usando.
* Comprobar la compatibilidad de tarjetas y controladores de gráficos:
    * Pruebe el puerto HDMI de su PC con un monitor de PC. Algunos equipos pueden tener más de un puerto HDMI y no todos pueden estar activos.
    * Si el equipo tiene una unidad de procesamiento de gráficos (iGPU) integrada y una unidad de procesamiento de gráficos discretos (dGPU), asegúrese de que está conectado al puerto HDMI de su dGPU.
    * Compruebe la versión del controlador de GPU. Asegúrese de que es reciente, pero también preste atención a los nuevos problemas de rendimiento y compatibilidad y a las regresiones en los nuevos controladores.
    * Si usa la realidad mixta en un equipo portátil y ha instalado un controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica, intente cambiar al controlador de la tarjeta gráfica más reciente que se proporciona en el sitio web del fabricante del equipo o en Windows Update.
    * Si tiene varios monitores de equipos conectados al equipo, intente desconectar temporalmente todo el monitor, excepto un equipo.
    * Si ha establecido una frecuencia de actualización personalizada para el monitor de PC, intente revertir temporalmente a una frecuencia de actualización estándar, como 60 Hz.
    * Si ha cambiado recientemente la tarjeta gráfica sin reinstalar Windows, compruebe que el monitor de auriculares todavía tiene instalado el controlador correcto. Con el casco enchufado, confirme que aparece "auricular de realidad mixta" en el nodo monitores de Device Manager.
    * Si el equipo tiene una tarjeta gráfica de NVIDIA, asegúrese de que el software 3D Vision de NVIDIA esté deshabilitado.
    * En algunas tarjetas de gráficos (especialmente tarjetas más antiguas), es posible que el puerto HDMI no admita HDMI 2,0 o que no sea totalmente compatible con Windows Mixed Reality. Intente usar el DisplayPort de la tarjeta gráfica con un [adaptador de displayport 1,2 a HDMI 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * Los equipos HP Omen con el número de producto de HP 1RJ99EA # ABU tienen puertos HDMI que no son compatibles con Windows Mixed Reality (Abra el "Asistente de soporte técnico de HP" y el número se mostrará en la parte inferior de la aplicación).
    * Si el equipo tiene una tarjeta gráfica AMD R9-series y está usando un casco de la realidad mixta de Samsung, actualice el firmware del casco a la versión 1.0.8 o posterior o posterior para usar el puerto HDMI de la tarjeta gráfica con los auriculares.
    * Si usa un libro de superficie 2, asegúrese de que está usando el [adaptador de USB-C de la superficie de Surface](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
* Busque un problema de hardware con auriculares de realidad mixta:
    * Para confirmar o descartar problemas de hardware con el casco, conecte el casco de realidad mixta a otro equipo.
    * Compruebe los problemas de configuración y compatibilidad de PC primero, ya que los síntomas son similares.
* Asegúrese de que el cable USB esté conectado a un puerto USB 3,0 o superior. Los puertos USB 3,0 tienen SS (súper velocidad) junto a ellos y a menudo están en color azul.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>En ocasiones, la pantalla se vuelve negra después de algún uso

* Intente deshabilitar las características de suspensión de USB o de ahorro de energía en su PC. Por ejemplo, en **configuración > sistema > Power & Sleep > suspensión [selectiva de USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)**, la configuración "permitir que el equipo apague este dispositivo para ahorrar energía" en Device Manager y cualquier configuración de ahorro de energía USB en el firmware del equipo.
* Desconecte temporalmente cualquier otro dispositivo USB y periféricos conectados al equipo.
* Compruebe que la versión del controlador de GPU es reciente y compruebe si hay nuevos problemas de rendimiento y compatibilidad y regresiones en los nuevos controladores.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Una de las pantallas del casco es negra

* Si usa un adaptador HDMI, asegúrese de que es compatible con HDMI 2,0.
* Quite los cables de extensión USB y HDMI que esté usando.
* Asegúrese de que el controlador de gráficos esté actualizado.
* Pruebe el casco de realidad mixta en otro equipo.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>El casco muestra el azul y, a continuación, se reinicializa el portal de realidad mixta

Esto suele indicar un problema ocasional de confiabilidad de controlador USB en el equipo:

* Pruebe con otro puerto USB. El equipo puede tener varios controladores USB 3,0.
* Quite los cables de extensión (si procede).
* Desconecte el resto de dispositivos USB del equipo.
* Conecte un concentrador USB 3,0 alimentado externamente al equipo y conecte los auriculares a la central.
* Si utiliza un equipo de escritorio, considere la posibilidad de comprar una tarjeta PCIe USB 3,0 para agregar otra controladora USB a su PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>El casco hace que el equipo se bloquee o muestre una pantalla negra al iniciarse

En algunos equipos, al mantener el casco conectado antes de encender o reiniciar el equipo puede interferir con el proceso de inicio. El equipo podría seleccionar los auriculares que se muestran como el "monitor principal" para mostrar el progreso de inicio del equipo, no iniciarse correctamente o "colgar" o generar un código de error de bip. El comportamiento depende de la marca y el modelo de PC, o de la marca y el modelo de la tarjeta gráfica. Para solucionar este error:

* Conecte los auriculares a un puerto diferente de la tarjeta gráfica (puede que tenga que usar un adaptador para usar los demás puertos).
* Asegúrese de que el firmware de BIOS/UEFI del equipo está actualizado (pero actualice el firmware de BIOS/UEFI del equipo si está familiarizado con esto).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>El equipo o el casco muestran parpadeo, Flash o permanecen negros al usar un equipo Surface

* Asegúrese de que está usando un adaptador HDMI compatible con HDMI 2,0. Muchos adaptadores de HDMI anteriores solo admiten la resolución de 1080p, lo que no es suficiente para auriculares de realidad mixta.
* Asegúrese de que el controlador de gráficos esté actualizado. Consulte Windows Update y el sitio web del fabricante del equipo para obtener un controlador de gráficos actualizado.
* Algunos dispositivos Surface son incompatibles con Windows Mixed Reality. Más información sobre la [compatibilidad y los requisitos](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)de las superficies.

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La pantalla del casco no funciona después de apagar y realizar un inicio rápido

Desconecte el cable HDMI y el cable USB del casco y, a continuación, vuelva a conectarlos.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Los auriculares aparecen entrecortado, pero la ventana de vista previa del portal de realidad mixta aparece bien

* Asegúrese de que los recursos del sistema (CPU, memoria y unidad de disco duro) del equipo están disponibles y no los consume otra aplicación o proceso.
* Actualice el controlador de gráficos.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Obtengo un error "la clase de instalación no está presente o no es válida" en Device Manager

Si ve "sensores de HoloLens" con un signo de exclamación amarillo en Device Manager, seleccione el dispositivo para obtener más detalles. Si ve un mensaje que dice "los controladores de este dispositivo no están instalados. (Código 28): la clase de instalación no está presente o no es válida. Esto suele deberse a que el equipo está ejecutando [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). N las ediciones de Windows 10 no admiten la realidad mixta de Windows y deberá instalar una versión que no sea de N de Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Mi entorno WMR es vibrar o se repite cuando se mueve el cabezal y muestra Double Vision

En un equipo portátil con gráficos integrados y una GPU de NVIDIA, se produce un error después de un período de tiempo que parece hacer que un fotograma anterior se muestre después del fotograma siguiente, lo que da lugar a una doble visión cuanto más rápido mueve el cabezal en una guiñada, un tono o un desplazamiento. El problema parece estar en controladores después del controlador de gráficos Nvidia 436,48.  La instalación de este controlador corregirá el problema hasta que NVIDIA resuelva el problema en los controladores actualizados. Para obtener una instalación directa del controlador de gráficos de NVIDIA 436,48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Me inincómodo en el casco

Para obtener información general acerca de la comodidad en Windows Mixed Reality, vea [Windows mixed reality sobre el estado de los auriculares, la seguridad y la comodidad](wmr-health-safety-comfort.md). Para obtener más información sobre el casco específico, consulte con el fabricante del casco.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>¿Cómo puedo obtener una vista más clara en el casco?

Intente ajustar el ajuste del casco. Muévala hacia arriba y hacia abajo, o a la izquierda y a la derecha, a su esfera y ajuste las correas para que se sienta perfectamente.

Si el casco tiene un botón para ajustar la calibración, ajuste la configuración de la calibración. Si no es así, vaya a **configuración > realidad mixta > calidad visual** y ajuste la calibración allí. Para obtener más información sobre la calibración de un dispositivo específico, consulte con el fabricante del casco.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Con frecuencia, veo un borde negro alrededor de la vista del casco. A veces es como estoy mirando un túnel.

Esto significa que la aplicación no puede alcanzar la velocidad de fotogramas en el equipo y el sistema usa fotogramas anteriores para presentar la vista en el casco. Puesto que las aplicaciones solo representan la parte del mundo que está buscando, si no alcanzan las tarifas de fotogramas de forma coherente, el sistema intentará representar el mundo desde un punto de vista anterior y rellenará los detalles que faltan con negro. Si esto sucede con frecuencia:

1. Cierre o detenga todos los programas innecesarios para liberar memoria y CPU.
2. Reduzca los valores de configuración de la aplicación.
3. Vaya a **configuración > realidad mixta > pantalla de auriculares** para reducir la cantidad de detalle que se muestra en la Página principal de Windows Mixed Reality.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La vista del casco está vibrando y se repite mucho

Es posible que el sistema no pueda presentar contenido al casco o que el sistema de seguimiento esté experimentando problemas:

1. Abra el administrador de tareas para asegurarse de que el equipo tiene suficientes recursos de proceso. Debe tener un 80% de CPU libre, 400 MB de RAM y la e/s de disco debe ser inferior al 80%.
2. Asegúrese de que dispone de los controladores de gráficos más recientes para su hardware. Consulte la [sección controlador de gráficos](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Asegúrese de que el salón tenga suficiente luz.
4. Desconecte el dispositivo, cierre Windows Mixed Reality y conéctelo de nuevo.
5. Reinicia tu equipo.
6. Si el problema persiste, póngase en contacto [con el servicio de soporte al cliente](https://support.microsoft.com/).
