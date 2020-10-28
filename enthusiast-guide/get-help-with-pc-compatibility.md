---
title: Obtener ayuda con la compatibilidad de equipos en Windows Mixed Reality
description: Recursos de ayuda para problemas de compatibilidad de equipos cuando se trabaja con Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: 75d8ade12d5534a1eb86f36bcdd590539a6811b5
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683181"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtener ayuda con la compatibilidad de equipos en Windows Mixed Reality

Al configurar Windows Mixed Reality o ejecutar la aplicación de [comprobación de PC de Windows Mixed Reality](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) en el equipo, aparecerá un informe sobre si el equipo está listo para ejecutarlo. Estos son algunos detalles sobre lo que puede ver.

Para asegurarse de que puede ejecutar Mixed Reality, consulte [requisitos mínimos de compatibilidad de hardware de equipos](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

## <a name="youre-good-to-go"></a>Está listo

Buenas noticias: su equipo puede ejecutar Windows Mixed Reality. Pero tenga en cuenta que todavía hay variación entre el hardware y la configuración del equipo, por lo que la experiencia de realidad mixta podría no ser la misma en todos los equipos.

## <a name="supports-some-features"></a>Admite algunas características

El equipo debe ser capaz de ejecutar algunas experiencias de realidad mixta de Windows, pero es posible que no proporcione la mejor experiencia posible. Los gráficos podrían retrasarse, algunas aplicaciones y juegos podrían no funcionar bien y otros podrían no ejecutarse en absoluto. 

Estos son los mensajes que pueden aparecer y qué hacer con ellos:

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este equipo tiene una tarjeta gráfica integrada con una RAM de canal único

Las tarjetas gráficas integradas proporcionarán la mejor experiencia de Windows Mixed Reality en equipos con RAM de dos canales. Si tiene problemas de rendimiento, realice una de las siguientes acciones:

* Instale una [tarjeta de gráficos discretos compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Instale un Memory Stick adicional para crear RAM de canal dual.
* Cambie a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible

PCIe significa *interconexión de componentes periféricos Express* . Se trata de la conexión que utiliza un equipo para comunicarse con una tarjeta gráfica. Es posible que la configuración funcione, pero si surgen problemas, deberá cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality

Si surgen problemas, intente descargar un nuevo controlador de gráficos con Windows Update ( **Iniciar configuración de > > actualizar & seguridad > comprobar si hay actualizaciones** ) o vaya al sitio web del fabricante de su PC o de la tarjeta gráfica.

> [!div class="nextstepaction"]
> [Buscar actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality

Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality, ya que no tiene suficientes núcleos. Si Windows Mixed Reality no se ejecuta correctamente, reemplace el procesador por [uno compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o cambie a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Es posible que este equipo no tenga una configuración USB compatible

Si tiene problemas para ejecutar Windows Mixed Reality, intente lo siguiente:

* Conecte el casco a otro puerto USB, si está disponible.
* Si eso no funciona, desinstale el controlador USB actual del equipo y, a continuación, vuelva a instalar un controlador de Microsoft:

1. Seleccione **Inicio** y, a continuación, escriba "Administrador de dispositivos" en el cuadro de **búsqueda** .
2. Seleccione **Device Manager** de los resultados.
3. Expanda la categoría de controladoras de bus serie universal, examine los dispositivos enumerados y desinstale los controladores que no sean compatibles.
    * Si la lista incluye un elemento "controlador de host extensible" que no tiene "Microsoft" al final del nombre del dispositivo, ese controlador no es compatible con Windows Mixed Reality. Tendrá que desinstalarlo. Para desinstalar un controlador, haga clic con el botón derecho en el dispositivo en la lista y seleccione **desinstalar dispositivo** . Active la casilla **eliminar el software de controlador para este dispositivo** y, a continuación, seleccione **desinstalar** .
    * Si la lista incluye un elemento "controlador de host extensible" que incluye "ETRON" en el nombre, el controlador USB no es compatible con Windows Mixed Reality. Deberá usar un puerto USB diferente en el equipo o adquirir otro controlador de host USB 3,0.
4. Reinicia tu equipo.
5. Vuelva a Device Manager y busque el elemento de controlador de host extensible de nuevo. Si ahora ve "Microsoft" al final del nombre del dispositivo, está listo. Si no es así, repita los pasos de desinstalación para quitar cualquier versión adicional que no sea de Microsoft del controlador.

* Si todavía no funciona, agregue una tarjeta USB PCIe a su PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este equipo no tiene Bluetooth 4,0 para los controladores

Bluetooth 4,0 es necesario para los controladores de movimiento de realidad mixta en algunos auriculares. Todavía puede usar Windows Mixed Reality con un controlador Xbox o con un mouse y un teclado, o puede usar un adaptador de Bluetooth USB para conectar controladores de movimiento al equipo. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>En función de los auriculares, es posible que necesite un adaptador de Bluetooth para usar los controladores de movimiento.

Algunos auriculares tienen Bluetooth integrado para que los controladores puedan emparejarse directamente con los auriculares. Otros requieren una radio Bluetooth en el equipo (o un dongle independiente) para usar los controladores de movimiento. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este equipo no tiene un puerto USB autoalimentado

Se necesita un puerto USB 3,0 autoalimentado para conectar un casco de realidad mixta de Windows. Conecte un concentrador USB 3,0 equipado al equipo y úselo para conectar el casco.

### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Este equipo debería funcionar, pero tendrá la mejor experiencia con un procesador Intel® de alto rendimiento.

Este equipo debería funcionar, pero un procesador Intel de alto rendimiento le proporcionará la mejor experiencia. Se recomienda una octava generación Intel® Core™ o la séptima generación Intel® Core™ procesador i5.

## <a name="cant-run-windows-mixed-reality"></a>No se puede ejecutar Windows Mixed Reality

Estos son los mensajes que pueden aparecer y qué hacer con ellos:

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La tarjeta gráfica de este equipo no funcionará con Windows Mixed Reality

La tarjeta gráfica de este equipo no es compatible con Windows Mixed Reality. Deberá agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality

El controlador de gráficos de este equipo no funcionará con Windows Mixed Reality. Intente descargar un nuevo controlador de gráficos mediante Windows Update ( **Iniciar configuración de > > actualizar & seguridad > comprobar si hay actualizaciones** ) o ir al sitio web del fabricante de su PC o de la tarjeta gráfica. 

> [!div class="nextstepaction"]
> [Buscar actualizaciones](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Si eso no funciona, deberá agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>El procesador de este equipo no funcionará con Windows Mixed Reality

El procesador de este equipo no es compatible con las instrucciones AVX/Popcnt. Para ejecutar Windows Mixed Reality, deberá reemplazarlo por una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este equipo no tiene suficiente espacio libre en disco para ejecutar Windows Mixed Reality

Windows Mixed Reality requiere 10 GB de espacio libre en disco para la instalación y el mejor rendimiento. Libere espacio en la unidad y vuelva a intentar realizar la instalación.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Este equipo está ejecutando una edición de Windows que no es compatible con Windows Mixed Reality

Windows Mixed Reality funciona en Windows 10 Home y Windows 10 Pro. Deberá instalar una de esas ediciones para poder usar Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este equipo no está ejecutando la versión más reciente de Windows 10

Windows Mixed Reality requiere Windows 10 Fall Creators Update. [Actualice el equipo](https://support.microsoft.com/help/4028685) e inténtelo de nuevo.

### <a name="this-pc-has-no-usb-30-port"></a>Este equipo no tiene un puerto USB 3,0

Necesitará un puerto USB 3,0 para conectar un auricular de Windows Mixed Reality. Si utiliza un equipo de escritorio, agregue una tarjeta USB PCIe. Si usa un equipo portátil, debe cambiar a un [equipo compatible](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>No se puede ejecutar esta aplicación a través de escritorio remoto

Para usar Windows Mixed Reality, se conectará un equipo con un monitor. Si usa una máquina virtual o no tiene un monitor, pruebe a usar un adaptador de pantalla virtual. Se trata de un dispositivo que se conecta al DisplayPort del PC y emula una pantalla del equipo. 

## <a name="getting-the-best-performance"></a>Obtención del mejor rendimiento

Algunas configuraciones de hardware pueden provocar problemas de rendimiento con Windows Mixed Reality. Para problemas como la carga lenta, los objetos visuales entrecortado o la mala calidad visual, Pruebe estas correcciones comunes:

* Cierre todas las aplicaciones abiertas que se ejecutan en el escritorio de su PC.
* Si usa un adaptador de USB-C o DisplayPort a HDMI, pruebe con otro. Consulte los adaptadores recomendados
* Si hay monitores adicionales conectados a la tarjeta gráfica del PC, desconéctelos.
* Intente descargar algunas aplicaciones de realidad mixta diferentes de la tienda Windows; algunas pueden funcionar mejor con la configuración del equipo.

> [!NOTE]
> Si ve un mensaje que indica "esta configuración de hardware podría funcionar con Windows Mixed Reality, pero aún no se ha probado", puede que haya problemas de rendimiento al ejecutar Windows Mixed Reality para sesiones largas.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas](troubleshooting-windows-mixed-reality.md)