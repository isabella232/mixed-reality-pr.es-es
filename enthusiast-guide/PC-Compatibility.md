---
title: PC de Windows Mixed Reality comprobar aplicación
description: Cómo buscar y usar el PC de Windows Mixed Reality comprobar la aplicación para probar la compatibilidad del equipo antes de adquirir un casco de la realidad mixta de Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, compatible, compatibilidad, equipo, requisitos del sistema
appliesto:
- Windows 10
ms.openlocfilehash: 464a2709600f7fff076053026797ce809b8fbf73
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340633"
---
# <a name="windows-mixed-reality-pc-check-app"></a>PC de Windows Mixed Reality comprobar aplicación

La aplicación **[Windows Mixed Reality PC check](windows-mixed-reality-pc-check-app.md)** es la mejor manera de asegurarse de que su equipo está listo para ejecutar Windows Mixed Reality.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Después de ejecutar la aplicación, recibirá uno de los siguientes mensajes:

* **Está listo.** Su equipo tiene lo que se necesita para ejecutar Windows Mixed Reality.
* **Está casi ahí.** Es posible que este equipo pueda ejecutar Windows Mixed Reality, pero puede que algunas características estén limitadas.
* **No se puede ejecutar Mixed Reality.** Este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality.

A continuación, obtendrá un análisis del equipo con el hardware, los controladores y el sistema operativo necesarios.
![Captura de pantalla de la comprobación de PC de Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icono</th><th>Qué significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">El equipo pasa el elemento necesario.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Puede haber problemas con su equipo para el requisito determinado. Si tiene problemas, es posible que tenga que solucionar problemas o actualizar el equipo.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">El equipo no cumple los requisitos del elemento especificado.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obtener ayuda con los resultados de la comprobación de equipos de Windows Mixed Reality

Al configurar Windows Mixed Reality o ejecutar la aplicación de comprobación de PC de Windows Mixed Reality en el equipo, aparecerá un informe sobre si el equipo está listo para ejecutarlo. Estos son algunos detalles sobre lo que puede ver.

### <a name="youre-good-to-go"></a>![Está listo](images/glyph-succeeded.png)

Buenas noticias: su equipo puede ejecutar Windows Mixed Reality. Pero tenga en cuenta que todavía hay variación entre el hardware y la configuración del equipo, por lo que la experiencia de realidad mixta podría no ser la misma en todos los equipos.

>[!NOTE]
>Si ve un mensaje que indica "esta configuración de hardware podría funcionar con Windows Mixed Reality, pero aún no se ha probado", puede que haya problemas de rendimiento al ejecutar Windows Mixed Reality para sesiones largas.

### <a name="youre-nearly-there"></a>![Está casi ahí](images/glyph-warning.png)

El equipo debe ser capaz de ejecutar Windows Mixed Reality, pero es posible que no proporcione la mejor experiencia posible. Los gráficos podrían retrasarse, algunas aplicaciones y juegos podrían no funcionar bien y otros podrían no ejecutarse en absoluto.

Estos son los mensajes que pueden aparecer y qué hacer con ellos:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este equipo tiene una tarjeta gráfica integrada con una RAM de canal único

Las tarjetas gráficas integradas proporcionarán la mejor experiencia de Windows Mixed Reality en equipos con RAM de dos canales. Si tiene problemas de rendimiento, realice una de las siguientes acciones:

* Instale una [tarjeta de gráficos discretos compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Instale un Memory Stick adicional para crear RAM de canal dual.
* Cambie a un [equipo compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible

PCIe significa *interconexión de componentes periféricos Express*. Se trata de la conexión que utiliza un equipo para comunicarse con una tarjeta gráfica. Es posible que la configuración funcione, pero si surgen problemas, deberá cambiar a un [equipo compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality

Si surgen problemas, intente descargar un nuevo controlador de gráficos con Windows Update ( **Iniciar configuración de > > actualizar & seguridad > comprobar si hay actualizaciones** ) o vaya al sitio web del fabricante de su PC o de la tarjeta gráfica.

Si eso no funciona, deberá agregar una [tarjeta gráfica compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o cambiar a un [equipo compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality

Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality, ya que no tiene suficientes núcleos. Si Windows Mixed Reality no se ejecuta correctamente, reemplace el procesador por [uno compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o cambie a un [equipo compatible](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Es posible que este equipo no tenga una configuración USB compatible

Si tiene problemas para ejecutar Windows Mixed Reality, intente lo siguiente:

* Conecte el casco a otro puerto USB, si está disponible.
* Si eso no funciona, desinstale el controlador USB actual del equipo y, a continuación, vuelva a instalar un controlador de Microsoft:

1. Seleccione **Inicio** y, a continuación, escriba **"Administrador de dispositivos"** en el cuadro de búsqueda.
1. Seleccione **Device Manager** de los resultados.
1. Expanda la categoría de controladoras de bus serie universal, examine los dispositivos enumerados y desinstale los controladores que no sean compatibles. 
 * Si la lista incluye un elemento "controlador de host extensible" que no tiene "Microsoft" al final del nombre del dispositivo, ese controlador no es compatible con Windows Mixed Reality. Tendrá que desinstalarlo. Para desinstalar un controlador, haga clic con el botón derecho en el dispositivo en la lista y seleccione **desinstalar dispositivo**. Active la casilla **eliminar el software de controlador para este dispositivo** y, a continuación, seleccione **desinstalar**.
 * Si la lista incluye un elemento "controlador de host extensible" que incluye "ETRON" en el nombre, el controlador USB no es compatible con Windows Mixed Reality. Deberá usar un puerto USB diferente en el equipo o adquirir otro controlador de host USB 3,0.
1. Reinicia tu equipo. 
1. Vuelva a Device Manager y busque el elemento de controlador de host extensible de nuevo. Si ahora ve "Microsoft" al final del nombre del dispositivo, está listo. Si no es así, repita los pasos de desinstalación para quitar cualquier versión adicional que no sea de Microsoft del controlador.
* Si todavía no funciona, agregue una tarjeta USB PCIe a su PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este equipo no tiene Bluetooth 4,0 para los controladores.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este equipo no tiene un puerto USB autoalimentado.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Este equipo debería funcionar, pero tendrá la mejor experiencia con un procesador de® Intel de alto rendimiento.

### <a name="cant-run-mixed-reality"></a>![No se puede ejecutar la realidad mixta](images/glyph-error.png)

 [Obtener ayuda con los resultados de la comprobación de equipos de Windows Mixed Reality](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
