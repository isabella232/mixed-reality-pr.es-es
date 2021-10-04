---
title: Obtención de ayuda con la compatibilidad de equipos
description: Manténgase al día con los recursos para resolver problemas de compatibilidad de equipos al trabajar con Windows Mixed Reality aplicaciones y dispositivos.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 1a07326da871eead6b13fe8350f37a22f8d27c23
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436569"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtenga ayuda con la compatibilidad de PC en Windows Mixed Reality

Al configurar la Windows Mixed Reality o usar el Portal de realidad mixta [,](install-windows-mixed-reality.md)se obtiene un informe sobre si el equipo está a la altura de la tarea. Hemos desglosado detalles específicos sobre lo que puede ver en las secciones siguientes.

Antes de continuar, pruebe las correcciones más comunes siguientes: 

> [!div class="checklist"]
> * Asegúrese de que el equipo cumple los requisitos [mínimos de compatibilidad de hardware del equipo.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Compruebe que la tarjeta [gráfica y el procesador](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) son compatibles
> * Comprobación de la [lista de adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Actualice el controlador de gráficos seleccionando Iniciar **> Configuración > actualizar & seguridad > Buscar actualizaciones** 

Si desea ponerse en contacto [](https://answers.microsoft.com)con la [](https://support.microsoft.com/contactus/)comunidad, póngase en contacto con el soporte técnico o consulte la información [de solución de](troubleshooting-windows-mixed-reality.md) problemas.

## <a name="youre-good-to-go"></a>Ya puede ir.

Buenas noticias: si ve el mensaje **You're good to go** (Está bien para ir), el equipo puede ejecutar Windows Mixed Reality. Todavía hay variación entre el hardware del equipo y la configuración, por lo que Mixed Reality experiencia podría no ser la misma en todos los equipos.

## <a name="supports-some-features"></a>Admite algunas características

Si ve el  mensaje Admite algunas características, el equipo puede ejecutar algunas experiencias Windows Mixed Reality, pero es posible que no proporcione la mejor experiencia posible. Entre las posibles desventajas se incluyen los gráficos de retraso, los aciertos de rendimiento y algunas aplicaciones y juegos que no se pueden ejecutar en absoluto. A continuación se muestran los mensajes que puede ver y qué hacer al respecto:

* [Este equipo tiene una tarjeta gráfica integrada con RAM de un solo canal](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Es posible que este equipo no tenga una configuración USB compatible](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Este equipo no tiene Bluetooth 4.0 para controladores](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [Dependiendo del casco, es posible que necesite un adaptador Bluetooth para usar controladores de movimiento.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Este equipo no tiene un puerto USB auto-powered](#this-pc-doesnt-have-a-self-powered-usb-port)
* [La tarjeta gráfica de este equipo no funcionará con Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [El procesador de este equipo no funcionará con Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Este equipo no tiene suficiente espacio libre en disco para ejecutar Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Este equipo ejecuta una edición de Windows que no admite Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Este equipo no ejecuta la versión más reciente de Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Este equipo no ejecuta la versión más reciente de Windows 11](#this-pc-isnt-running-the-latest-version-of-windows-11)
* [Este equipo no tiene puerto USB 3.0](#this-pc-has-no-usb-30-port)
* [No se puede ejecutar esta aplicación a través de Escritorio remoto](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este equipo tiene una tarjeta gráfica integrada con RAM de un solo canal

Las tarjetas gráficas integradas proporcionarán la mejor Windows Mixed Reality experiencia en equipos con RAM de doble canal. Si tiene problemas de rendimiento:

> [!div class="checklist"]
> * Instalación de una [tarjeta gráfica discreta compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Instalación de una ram stick adicional para crear ram de doble canal
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible

PCIe significa *Interconexión* rápida de componentes periféricos, que es la conexión que usa un equipo para comunicarse con una tarjeta gráfica. La configuración puede funcionar, pero si tiene problemas, tendrá que cambiar a un [equipo compatible.](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality

Pruebe a descargar un nuevo controlador de gráficos Windows Actualizar mediante:

> [!div class="checklist"]
> * Al seleccionar **Iniciar > Configuración > actualizar & seguridad > buscar** actualizaciones o ir al sitio web del fabricante de su PC o tarjeta gráfica
> * [Comprobación de actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá:

> [!div class="checklist"]
> * Adición de [una tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality

Es posible que el procesador del equipo no funcione bien Windows Mixed Reality porque no tiene suficientes núcleos. Si Windows Mixed Reality no se ejecuta bien:

> [!div class="checklist"]
> * Reemplazar el procesador por uno [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Es posible que este equipo no tenga una configuración USB compatible

Para problemas de ejecución Windows Mixed Reality:

> [!div class="checklist"]
> * Consulte la documentación [de los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para ver soluciones a problemas de compatibilidad comunes.
> * Considere la posibilidad de [usar un concentrador USB con tecnología externa](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Si los problemas persisten:

> [!div class="checklist"]
> * Conecte el casco a otro puerto USB, si tiene uno disponible.
> * Si esto no funciona, desinstale el controlador USB actual del equipo y, a continuación, vuelva a instalar un controlador de Microsoft:

1. Seleccione **Iniciar** y, a continuación, escriba "Administrador de dispositivos" en el **cuadro** De búsqueda.
2. Seleccione **Administrador de dispositivos** en los resultados.
3. Expanda la categoría controladores de bus serie universal, mire los dispositivos enumerados y desinstale los controladores incompatibles.
    * Si la lista incluye un elemento "Controlador de host eXtensible" que no tiene "Microsoft" al final del nombre del dispositivo, ese controlador no es compatible con Windows Mixed Reality. Deberá desinstalarlo. Para desinstalar un controlador, haga clic con el botón derecho en el dispositivo de la lista y seleccione **Desinstalar dispositivo.** Active la **casilla Eliminar el software del controlador para este dispositivo** y, a continuación, seleccione **Desinstalar**.
    * Si la lista incluye un elemento "Controlador de host eXtensible" que incluye "Etrón" en el nombre, ese controlador USB no es compatible con Windows Mixed Reality. Deberá usar un puerto USB diferente en el equipo o adquirir un controlador host USB 3.0 diferente.
4. Reinicia tu equipo.
5. Vuelva a Administrador de dispositivos y busque de nuevo el elemento Controlador de host eXtensible. Si ahora ve "Microsoft" al final del nombre del dispositivo, puede ir. Si no es así, repita los pasos de desinstalación para quitar las versiones adicionales que no son de Microsoft del controlador.

> [!div class="checklist"]
> * Si sigue sin funcionar, agregue una tarjeta USB PCIe al equipo.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este equipo no tiene Bluetooth 4.0 para controladores

Los cascos de Windows Mixed Reality 2018 y versiones más recientes ya tienen el Bluetooth integrado, pero si tiene cascos antiguos, se requiere bluetooth 4.0 para los controladores de movimiento de realidad mixta. Todavía puedes usar Windows Mixed Reality un controlador [de Xbox,](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)un [mouse](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)y un teclado, o un adaptador Bluetooth USB para conectar controladores de [movimiento](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) al equipo. [Consulte los adaptadores recomendados.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Dependiendo del casco, es posible que necesite un adaptador Bluetooth para usar controladores de movimiento.

Algunos cascos tienen Bluetooth integrados para que los controladores puedan emparejarse directamente con los cascos. Otros requieren una Bluetooth radio en el equipo (o un llavete independiente) para usar controladores de movimiento. Para obtener más información, vea la [página adaptadores recomendados.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este equipo no tiene un puerto USB auto-powered

Se necesita un puerto USB 3.0 autoconectado para conectar un casco Windows Mixed Reality dispositivo. Conectar un [concentrador USB 3.0 con](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) tecnología al equipo y úselo para conectar el casco.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La tarjeta gráfica de este equipo no funcionará con Windows Mixed Reality

La tarjeta gráfica de este equipo no es compatible con Windows Mixed Reality. Necesitará:

> [!div class="checklist"]
> * Adición de [una tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality

El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality. Pruebe a descargar un nuevo controlador de gráficos Windows Actualizar mediante:

> [!div class="checklist"]
> * Al seleccionar **Iniciar > Configuración > actualizar & seguridad > buscar** actualizaciones o ir al sitio web del fabricante de su PC o tarjeta gráfica
> * [Comprobación de actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá:

> [!div class="checklist"]
> * Adición de [una tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>El procesador de este equipo no funcionará con Windows Mixed Reality

El procesador de este equipo no admite instrucciones avx/popcnt. Para ejecutar Windows Mixed Reality, deberá:

> [!div class="checklist"]
> * Reemplázla por una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Cambio a un [equipo compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este equipo no tiene suficiente espacio libre en disco para ejecutar Windows Mixed Reality

Windows Mixed Reality requiere 10 GB de espacio libre en disco para la instalación y el mejor rendimiento. Borre algo de espacio en la unidad e intente volver a configurarla desde el principio.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Este equipo ejecuta una edición de Windows que no admite Windows Mixed Reality

Windows Mixed Reality funciona en [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab), [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)y Windows [11](https://www.microsoft.com/software-download/windows11). Deberá instalar una de esas ediciones para usar Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este equipo no ejecuta la versión más reciente de Windows 10

Windows Mixed Reality requiere el Windows 10 Fall Creators Update. [Actualice el equipo e](https://support.microsoft.com/help/4028685) inténtelo de nuevo.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-11"></a>Este equipo no ejecuta la versión más reciente de Windows 11

Windows Mixed Reality requiere la versión Windows 11 más reciente. [Actualice el equipo e](https://www.microsoft.com/software-download/windows11) inténtelo de nuevo.

### <a name="this-pc-has-no-usb-30-port"></a>Este equipo no tiene puerto USB 3.0

Necesitará un puerto USB 3.0 para conectar un casco Windows Mixed Reality dispositivo. Si usa un equipo de escritorio, agregue una tarjeta USB PCIe. En el caso de los equipos portátiles, deberá cambiar a un [equipo compatible.](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)

### <a name="you-cant-run-this-app-via-remote-desktop"></a>No se puede ejecutar esta aplicación a través de Escritorio remoto

Para usar Windows Mixed Reality, necesita un equipo con un monitor conectado. Si usa una máquina virtual o no tiene un monitor, pruebe a usar un adaptador de pantalla virtual. Se trata de un dispositivo que se conecta a DisplayPort del equipo y emula una pantalla de equipo.

## <a name="getting-the-best-performance"></a>Obtención del mejor rendimiento

Algunas configuraciones de hardware pueden causar problemas de rendimiento con Windows Mixed Reality. Para problemas como la carga lenta, los objetos visuales lentos o la calidad visual deficiente, pruebe estas correcciones comunes:

* Cierre las aplicaciones abiertas que se ejecutan en el escritorio del equipo
* Si usa un adaptador USB-C o DisplayPort a HDMI, pruebe otro diferente. Consulte los adaptadores recomendados.
* Si hay monitores adicionales conectados a la tarjeta gráfica del equipo, desconéctelos.
* Pruebe a descargar algunas aplicaciones de realidad mixta diferentes desde Windows Store; algunas pueden funcionar mejor con la configuración del equipo.
* Consulte nuestra documentación [de preguntas de rendimiento.](performance-questions.md)

Si sigue teniendo problemas de rendimiento, actualice la siguiente configuración [Windows Mixed Reality](set-up-windows-mixed-reality.md) configuración para una experiencia de usuario óptima:

* Experiencia
* Solución
* Velocidad de fotogramas
* Calibración

> [!NOTE]
> Si ve un mensaje que dice "Esta configuración de hardware podría funcionar con Windows Mixed Reality, pero aún no se ha probado", podría encontrarse con algunos problemas de rendimiento al ejecutar Windows Mixed Reality para sesiones largas.

## <a name="working-with-steamvr"></a>Trabajar con SteamVR

Disfrutar de juegos de SteamVR es una excelente manera de experimentar todo lo que ofrece VR. Sin embargo, querrá asegurarse de que está obteniendo el mejor [rendimiento](performance-questions.md) del dispositivo inmersivo. Después de instalar [Steam:](https://store.steampowered.com/about)

* Siga las instrucciones para [usar SteamVR con Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Instalación de las [aplicaciones de prueba de rendimiento de SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Siguiente punto de comprobación de VR

Si sigue el recorrido de realidad virtual que hemos diseñado, está casi listo para comprar un dispositivo. Desde aquí, puede continuar hasta la última antes de comprar el punto de control:

> [!div class="nextstepaction"]
> [Preguntas más frecuentes sobre la compra](before-you-buy-faqs.md)

O bien, vaya directamente a la sección de introducción:

> [!div class="nextstepaction"]
> [Configuración de Windows Mixed Reality](set-up-windows-mixed-reality.md)

Siempre puede volver al recorrido de [realidad virtual](vr-journey.md) en cualquier momento.