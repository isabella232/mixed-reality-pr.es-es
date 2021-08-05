---
title: Windows Mixed Reality Aplicación PC Check
description: Cómo buscar y usar la aplicación Windows Mixed Reality PC Check para probar la compatibilidad del equipo antes de comprar un casco Windows Mixed Reality dispositivo.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, compatible, compatibilidad, PC, requisitos del sistema
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188054"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality Aplicación PC Check

La **[Windows Mixed Reality pc check](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** es la mejor manera de asegurarse de que el equipo está listo para ejecutarse Windows Mixed Reality. La Windows Mixed Reality pc check solo funciona en equipos con al menos Windows 10 versión 1607 instalada. Para comprobar la versión de Windows, escriba "winver" en la barra de búsqueda y ejecute el comando . En Windows 10 versiones anteriores a la 1607, la aplicación seguirá a aparecer en la Tienda, pero recibirá un error al intentar instalar.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Después de ejecutar la aplicación, verá uno de los mensajes siguientes:

* **Está bien para ir.** El equipo tiene lo que se necesita para ejecutar Windows Mixed Reality.
* **Casi está allí.** Este equipo puede ejecutar Windows Mixed Reality, pero algunas características pueden ser limitadas.
* **No se puede ejecutar la realidad mixta.** Este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality.

A continuación, se obtiene un análisis del equipo con el hardware, los controladores y el sistema operativo necesarios.
![Captura de pantalla de Windows Mixed Reality PC Check](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icono</th><th>Qué significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">El equipo pasa el elemento necesario.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Puede haber problemas con el equipo para el requisito dado. Si tiene algún problema, es posible que tenga que solucionar problemas o actualizar el equipo.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">El equipo no cumple los requisitos del elemento especificado.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obtener ayuda con los resultados Windows Mixed Reality pc Check

Al configurar el equipo, se obtiene un informe de compatibilidad Windows Mixed Reality ejecutar la aplicación Windows Mixed Reality PC Check. Estos son algunos detalles sobre lo que puede ver.

### <a name="youre-good-to-go"></a>![Está bien para ir](images/glyph-succeeded.png)

Buenas noticias: el equipo puede ejecutar Windows Mixed Reality. Tenga en cuenta que todavía hay variación entre el hardware y la configuración del equipo. Es posible que la experiencia de realidad mixta no sea la misma en todos los PC.

>[!NOTE]
>Si ve un mensaje que dice "Esta configuración de hardware puede funcionar con Windows Mixed Reality, pero aún no se ha probado", podría encontrarse con algunos problemas de rendimiento al ejecutar Windows Mixed Reality para sesiones largas.

### <a name="youre-nearly-there"></a>![Casi está allí.](images/glyph-warning.png)

El equipo debe ser capaz de ejecutar Windows Mixed Reality, pero es posible que no proporcione la mejor experiencia posible. Los gráficos pueden presentar retrasos, es posible que algunas aplicaciones y juegos no funcionen bien y que algunos no se ejecuten en absoluto.

Estos son los mensajes que puede ver y qué hacer al respecto:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este equipo tiene una tarjeta gráfica integrada con RAM de un solo canal

Las tarjetas gráficas integradas proporcionarán la mejor Windows Mixed Reality experiencia en equipos con RAM de doble canal. Si tiene problemas de rendimiento:

* Instale una [tarjeta gráfica discreta compatible.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Instale una ram stick adicional para crear ram de doble canal.
* Cambie a un [equipo compatible.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este equipo tiene una configuración de gráficos híbrida con un vínculo PCIe incompatible

PCIe es el nombre *de La interconexión de componentes periféricos express.* Esta es la conexión que usa un equipo para comunicarse con una tarjeta gráfica. Es posible que la configuración funcione, pero si tiene problemas, deberá cambiar a un [equipo compatible.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el controlador de gráficos de este equipo no funcione bien con Windows Mixed Reality

Si tiene problemas, intente descargar un nuevo controlador de gráficos mediante Windows Update (Iniciar > Configuración > Actualizar & >**Buscar** actualizaciones) o vaya al sitio web del fabricante del equipo o del fabricante de tarjetas gráficas.

Si esto no funciona, deberá agregar una tarjeta gráfica [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o cambiar a un [equipo compatible.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Es posible que el procesador de este equipo no funcione bien con Windows Mixed Reality

Es posible que el procesador de este equipo no funcione bien Windows Mixed Reality, ya que no tiene suficientes núcleos. Si Windows Mixed Reality no se ejecuta bien, actualice a uno [compatible](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o cambie a un [equipo compatible.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Es posible que este equipo no tenga una configuración USB compatible

Si tiene problemas para ejecutar Windows Mixed Reality:

* Conecte el casco a otro puerto USB, si está disponible.
* Si eso no funciona, desinstale el controlador USB actual del equipo y, a continuación, vuelva a instalar un controlador de Microsoft:

1. Seleccione **Iniciar** y, a continuación, **escriba "Administrador de dispositivos"** en el cuadro De búsqueda.
1. Seleccione **Administrador de dispositivos** en los resultados.
1. Expanda la categoría controladores de bus serie universal, mire los dispositivos enumerados y desinstale los controladores incompatibles. 
 * Si la lista incluye un elemento "Controlador de host eXtensible" sin "Microsoft" al final del nombre del dispositivo, el controlador no es compatible con Windows Mixed Reality. Deberá desinstalarlo. Para desinstalar un controlador, haga clic con el botón derecho en el dispositivo de la lista y seleccione **Desinstalar dispositivo.** Active la **casilla Eliminar el software del controlador para este dispositivo** y, a continuación, seleccione **Desinstalar**.
 * Si la lista incluye un elemento "Controlador de host eXtensible" que incluye "Etrón" en el nombre, ese controlador USB no es compatible con Windows Mixed Reality. Deberá usar un puerto USB diferente en el equipo o adquirir un controlador host USB 3.0 diferente.
1. Reinicia tu equipo. 
1. Vuelva a Administrador de dispositivos y busque de nuevo el elemento Controlador de host eXtensible. Si ahora ve "Microsoft" al final del nombre del dispositivo, puede ir. Si no es así, repita los pasos de desinstalación para quitar las versiones adicionales que no son de Microsoft del controlador.
* Si sigue sin funcionar, agregue una tarjeta USB PCIe al equipo.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este equipo no tiene Bluetooth 4.0 para los controladores.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este equipo no tiene un puerto USB auto-powered.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Este equipo debería funcionar, pero tendrá la mejor experiencia con un procesador Intel ® alto rendimiento.

### <a name="cant-run-mixed-reality"></a>![No se puede ejecutar la realidad mixta](images/glyph-error.png)

 [Obtener ayuda con los resultados Windows Mixed Reality pc Check](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
