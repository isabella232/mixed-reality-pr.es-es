---
title: Obtener ayuda con la compatibilidad de equipos en Windows Mixed Reality
description: Recursos de ayuda para problemas de compatibilidad de equipos cuando se trabaja con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: a3d8c21a6f9f94cbecca81915145603588e468ff
ms.sourcegitcommit: e944f24d2deb4433865cc8f6fd9305d6d9676f48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2021
ms.locfileid: "97971904"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtener ayuda con la compatibilidad de equipos en Windows Mixed Reality

Cuando esté configurando Windows Mixed Reality o usando el [portal de realidad mixta](install-windows-mixed-reality.md), obtendrá un informe sobre si el equipo depende de la tarea. Hemos desglosado detalles específicos sobre lo que puede ver en las secciones siguientes.

Antes de continuar, pruebe las siguientes soluciones más comunes: 

> [!div class="checklist"]
> * Asegúrese de que el equipo cumple los [requisitos mínimos de compatibilidad de hardware de equipos](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Compruebe que la [tarjeta gráfica y el procesador](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) son compatibles
> * Comprobación de la lista de [adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Actualice el controlador de gráficos seleccionando **inicio > configuración > actualizar & seguridad > comprobar si hay actualizaciones** 

Si desea ponerse en contacto con, puede solicitar a [la comunidad](https://answers.microsoft.com), [ponerse en contacto con el soporte técnico](https://support.microsoft.com/contactus/)o consultar la información de [solución de problemas](troubleshooting-windows-mixed-reality.md) .

## <a name="youre-good-to-go"></a>Está listo

Buena noticia, si ve el mensaje **está listo para ir** , su equipo puede ejecutar Windows Mixed Reality. Todavía hay variación entre el hardware y la configuración del equipo, por lo que la experiencia de realidad mixta podría no ser la misma en todos los equipos.

## <a name="supports-some-features"></a>Admite algunas características

Si ve el mensaje **admite algunas características** , el equipo puede ejecutar algunas experiencias de realidad mixta de Windows, pero es posible que no proporcione la mejor experiencia posible. Entre los posibles inconvenientes se incluyen gráficos atrasados, aciertos de rendimiento y algunas aplicaciones y juegos que no se pueden ejecutar en absoluto. Se muestran los mensajes que pueden aparecer y qué hacer a continuación:

* [Este equipo tiene una tarjeta gráfica integrada con una RAM de canal único](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Es posible que este equipo no tenga una configuración USB compatible](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Este equipo no tiene Bluetooth 4,0 para los controladores](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [En función de los auriculares, es posible que necesite un adaptador de Bluetooth para usar los controladores de movimiento.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Este equipo no tiene un puerto USB autoalimentado](#this-pc-doesnt-have-a-self-powered-usb-port)
* [La tarjeta gráfica de este equipo no funcionará con Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [El procesador de este equipo no funcionará con Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Este equipo no tiene suficiente espacio libre en disco para ejecutar Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Este equipo está ejecutando una edición de Windows que no es compatible con Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Este equipo no está ejecutando la versión más reciente de Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Este equipo no tiene un puerto USB 3,0](#this-pc-has-no-usb-30-port)
* [No se puede ejecutar esta aplicación a través de escritorio remoto](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este equipo tiene una tarjeta gráfica integrada con una RAM de canal único

Las tarjetas gráficas integradas proporcionarán la mejor experiencia de Windows Mixed Reality en equipos con RAM de dos canales. Si surgen problemas de rendimiento:

> [!div class="checklist"]
> * Instalación de una [tarjeta de gráficos discretos compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Instalación de un Memory Stick adicional para crear RAM de canal dual
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible

PCIe significa *interconexión de componentes periféricos Express*, que es la conexión que utiliza un equipo para comunicarse con una tarjeta gráfica. Es posible que la configuración funcione, pero si surgen problemas, deberá cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality

Intente descargar un nuevo controlador de gráficos mediante Windows Update por:

> [!div class="checklist"]
> * Seleccionar **inicio > configuración > actualizar & seguridad > buscar actualizaciones** o ir al sitio web del fabricante de su PC o tarjeta gráfica
> * [Buscar actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá hacer lo siguiente:

> [!div class="checklist"]
> * Agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality

El procesador de su PC podría no funcionar bien con Windows Mixed Reality porque no tiene suficientes núcleos. Si Windows Mixed Reality no se ejecuta correctamente:

> [!div class="checklist"]
> * Reemplazar el procesador por [uno compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Es posible que este equipo no tenga una configuración USB compatible

Para problemas al ejecutar Windows Mixed Reality:

> [!div class="checklist"]
> * Consulte la [documentación de los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obtener soluciones a problemas de compatibilidad comunes.
> * Considere la posibilidad de usar un [concentrador USB alimentado externamente](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Si los problemas continúan:

> [!div class="checklist"]
> * Conecte el casco a otro puerto USB, si tiene uno disponible.
> * Si eso no funciona, desinstale el controlador USB actual del equipo y, a continuación, vuelva a instalar un controlador de Microsoft:

1. Seleccione **Inicio** y, a continuación, escriba "Administrador de dispositivos" en el cuadro de **búsqueda** .
2. Seleccione **Device Manager** de los resultados.
3. Expanda la categoría de controladoras de bus serie universal, examine los dispositivos enumerados y desinstale los controladores que no sean compatibles.
    * Si la lista incluye un elemento "controlador de host extensible" que no tiene "Microsoft" al final del nombre del dispositivo, ese controlador no es compatible con Windows Mixed Reality. Tendrá que desinstalarlo. Para desinstalar un controlador, haga clic con el botón derecho en el dispositivo en la lista y seleccione **desinstalar dispositivo**. Active la casilla **eliminar el software de controlador para este dispositivo** y, a continuación, seleccione **desinstalar**.
    * Si la lista incluye un elemento "controlador de host extensible" que incluye "ETRON" en el nombre, el controlador USB no es compatible con Windows Mixed Reality. Deberá usar un puerto USB diferente en el equipo o adquirir otro controlador de host USB 3,0.
4. Reinicia tu equipo.
5. Vuelva a Device Manager y busque el elemento de controlador de host extensible de nuevo. Si ahora ve "Microsoft" al final del nombre del dispositivo, está listo. Si no es así, repita los pasos de desinstalación para quitar las versiones adicionales que no sean de Microsoft del controlador.

> [!div class="checklist"]
> * Si todavía no funciona, agregue una tarjeta USB PCIe a su PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este equipo no tiene Bluetooth 4,0 para los controladores

2018 y las versiones más recientes de los auriculares de Windows Mixed Reality ya tienen el Bluetooth integrado, pero si tiene auriculares más antiguos, se requiere Bluetooth 4,0 para los controladores de movimiento de realidad mixta. Todavía puede [usar Windows Mixed Reality con un controlador de Xbox](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), un [mouse y un teclado](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse), o un adaptador de [Bluetooth USB para conectar controladores de movimiento](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) al equipo. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>En función de los auriculares, es posible que necesite un adaptador de Bluetooth para usar los controladores de movimiento.

Algunos auriculares tienen Bluetooth integrado, por lo que los controladores pueden emparejarse directamente con los auriculares. Otros requieren una radio Bluetooth en el equipo (o un dongle independiente) para usar los controladores de movimiento. Para obtener más información, consulte la página de [adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este equipo no tiene un puerto USB autoalimentado

Se necesita un puerto USB 3,0 autoalimentado para conectar un casco de realidad mixta de Windows. Conecte un [concentrador USB 3,0 equipado](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) al equipo y úselo para conectar el casco.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La tarjeta gráfica de este equipo no funcionará con Windows Mixed Reality

La tarjeta gráfica de este equipo no es compatible con Windows Mixed Reality. Necesitará:

> [!div class="checklist"]
> * Agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality

El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality. Intente descargar un nuevo controlador de gráficos mediante Windows Update por:

> [!div class="checklist"]
> * Seleccionar **inicio > configuración > actualizar & seguridad > buscar actualizaciones** o ir al sitio web del fabricante de su PC o tarjeta gráfica
> * [Buscar actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá hacer lo siguiente:

> [!div class="checklist"]
> * Agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>El procesador de este equipo no funcionará con Windows Mixed Reality

El procesador de este equipo no es compatible con las instrucciones AVX/Popcnt. Para ejecutar Windows Mixed Reality, deberá hacer lo siguiente:

> [!div class="checklist"]
> * Reemplácelo por una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambiar a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este equipo no tiene suficiente espacio libre en disco para ejecutar Windows Mixed Reality

Windows Mixed Reality requiere 10 GB de espacio libre en disco para la instalación y el mejor rendimiento. Libere espacio en la unidad y, a continuación, intente configurar de nuevo desde el principio.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Este equipo está ejecutando una edición de Windows que no es compatible con Windows Mixed Reality

Windows Mixed Reality funciona en [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) y [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Deberá instalar una de esas ediciones para usar Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este equipo no está ejecutando la versión más reciente de Windows 10

Windows Mixed Reality requiere Windows 10 Fall Creators Update. [Actualice el equipo](https://support.microsoft.com/help/4028685) e inténtelo de nuevo.

### <a name="this-pc-has-no-usb-30-port"></a>Este equipo no tiene un puerto USB 3,0

Necesitará un puerto USB 3,0 para conectar un auricular de Windows Mixed Reality. Si utiliza un equipo de escritorio, agregue una tarjeta USB PCIe. En el caso de los equipos portátiles, deberá cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>No se puede ejecutar esta aplicación a través de escritorio remoto

Para usar Windows Mixed Reality, necesita un equipo con un monitor conectado. Si utiliza una máquina virtual o no tiene un monitor, pruebe a usar un adaptador de pantalla virtual. Se trata de un dispositivo que se conecta al DisplayPort del PC y emula una pantalla del equipo.

## <a name="getting-the-best-performance"></a>Obtención del mejor rendimiento

Algunas configuraciones de hardware pueden provocar problemas de rendimiento con Windows Mixed Reality. Para problemas como la carga lenta, los objetos visuales entrecortado o la mala calidad visual, Pruebe estas correcciones comunes:

* Cierre todas las aplicaciones abiertas que se ejecutan en el escritorio de su PC
* Si usa un adaptador de USB-C o DisplayPort a HDMI, pruebe con otro. Consulte los adaptadores recomendados
* Si hay monitores adicionales conectados a la tarjeta gráfica del PC, desconéctelos
* Intente descargar algunas aplicaciones de realidad mixta diferentes de la tienda Windows; algunas pueden funcionar mejor con la configuración del equipo
* Consulte nuestra [documentación sobre preguntas de rendimiento](performance-questions.md)

Si sigue teniendo problemas de rendimiento, actualice la siguiente configuración de [Windows Mixed Reality](set-up-windows-mixed-reality.md) para mejorar la experiencia del usuario:

* Experiencia
* Solución
* Velocidad de fotogramas
* Calibración

> [!NOTE]
> Si ve un mensaje que indica "esta configuración de hardware podría funcionar con Windows Mixed Reality, pero aún no se ha probado", puede que haya problemas de rendimiento al ejecutar Windows Mixed Reality para sesiones largas.

## <a name="working-with-steamvr"></a>Trabajar con SteamVR

Disfrutar de juegos de SteamVR es una excelente manera de experimentar todo lo que ofrece la VR. Sin embargo, querrá asegurarse de que está [obteniendo el mejor rendimiento](performance-questions.md) de su dispositivo envolvente. Después de haber instalado [vapor](https://store.steampowered.com/about):

* Siga las instrucciones para [usar SteamVR con Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md) .
* Instalación de las aplicaciones de [prueba de rendimiento de SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Siguiente punto de control de VR

Si está siguiendo el viaje de VR que hemos diseñado, está casi listo para comprar un dispositivo. Desde aquí, puede continuar hasta el último antes de comprar el punto de control:

> [!div class="nextstepaction"]
> [Preguntas más frecuentes sobre compras](before-you-buy-faqs.md)

O bien, vaya directamente a la sección Introducción:

> [!div class="nextstepaction"]
> [Configurar Windows Mixed Reality](set-up-windows-mixed-reality.md)

Siempre puede volver al [recorrido de VR](vr-journey.md) en cualquier momento.