---
title: Windows Mixed Reality y el nuevo Microsoft Edge
description: Obtenga información sobre el nuevo Microsoft Edge para la realidad mixta, incluido lo que se espera, las actualizaciones que se van a buscar y los problemas conocidos.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: Edge, nuevo, Web envolvente, Microsoft Edge, explorador, VR, 360, 360 video, 360 Viewer, webxr, webvr
ms.openlocfilehash: ef55ee564e0a7ea11aaaad62ebf259459454ab72
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010035"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>El nuevo Microsoft Edge para Windows Mixed Reality

El [nuevo Microsoft Edge ya está disponible para su descarga](https://blogs.windows.com/windowsexperience/?p=173496), pero los clientes también pueden [esperar una actualización futura para instalarlo con Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), siguiendo un enfoque de implementación medido en los próximos meses. 

Con esta noticia, **queríamos que los clientes de la realidad de Windows Mixed Reality sepan qué esperar del nuevo Microsoft Edge y mostraban las actualizaciones pendientes para mejorar la experiencia de exploración en Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Presentación del nuevo Microsoft Edge

El nuevo Microsoft Edge [adopta el proyecto de código abierto de cromo](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) en el escritorio para crear una mejor compatibilidad con los clientes y menos fragmentación de la web para los desarrolladores Web. También admitirá WebXR en el lanzamiento, el nuevo estándar para crear experiencias Web envolventes para los auriculares VR en lugar de WebVR.

>[!IMPORTANT]
>Al instalar Microsoft Edge en un dispositivo de Windows 10 actualizado, se reemplazará la versión anterior (heredada) del equipo.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Preparación para el nuevo Microsoft Edge

Los auriculares Windows Mixed Reality VR con auriculares que desean usar el nuevo Microsoft Edge en la Página principal de la realidad mixta deben **actualizarse a la versión 1903 o posterior de Windows 10 para ofrecer compatibilidad nativa con aplicaciones Win32 (como el nuevo Microsoft Edge)** en la Página principal de la realidad mixta. Active Windows Update o [Instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Para obtener la mejor experiencia posible de Microsoft Edge en la Página principal de la realidad mixta, también se recomienda esperar **algunas optimizaciones clave de Windows Mixed Reality para que la nueva Microsoft Edge llegue a la actualización acumulativa 2020-01 para Windows 10, versión 1903 (o posterior)**, que debe estar disponible en Windows Update a finales de enero.

>[!IMPORTANT]
>Si opta por descargar el nuevo Microsoft Edge antes de realizar estas actualizaciones, habrá algunos problemas conocidos con su comportamiento en Windows Mixed Reality (que puede leer a continuación).

## <a name="known-issues"></a>Problemas conocidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10, versión 1903 (o posterior)

- Iniciar cualquier aplicación de Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se incongele brevemente.
- El icono de Microsoft Edge desaparece del menú Inicio de Windows Mixed Reality (puede encontrarlo en la carpeta "aplicaciones clásicas").
- Las ventanas del Microsoft Edge anterior se siguen colocando en la Página principal de la realidad mixta, pero no se pueden usar. El intento de activar esas ventanas inicia el perímetro en la aplicación de escritorio.
- Al seleccionar un hipervínculo en la Página principal de realidad mixta, se inicia un explorador Web en el escritorio en lugar de la Página principal de realidad mixta.
- La aplicación WebVR Showcase está presente en la Página principal de la realidad mixta, a pesar de que WebVR ya no se admite.
- Mejoras generales en el inicio del teclado y los objetos visuales.

### <a name="monitor-and-input-handling-issues"></a>Problemas de control de entrada y supervisión

Después de realizar la actualización acumulativa 2020-01 para la versión 1903 (o posterior) de Windows 10, los monitores virtuales aparecerán como monitores físicos genéricos en la **configuración > sistema > Mostrar** durante las sesiones de realidad mixta de Windows. Algunos clientes, especialmente con más de un monitor físico, pueden notar problemas con el diseño del escritorio y el control de entrada como resultado.

**¿Por qué ocurre esto?**

La compatibilidad con aplicaciones Win32 clásicas en Windows Mixed Reality se presentó con la [actualización de Windows 10 de mayo de 2019](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Para habilitar esta compatibilidad, se debe crear un monitor virtual para hospedar la aplicación Win32. Cada vez que se inicia una nueva aplicación Win32, debe crearse otro monitor virtual. Desgraciadamente, la creación de un monitor virtual es una tarea intensiva que puede hacer que la pantalla del casco se incongele brevemente. Los clientes ofrecían comentarios de que se trata de una experiencia desagradable y molesta. Debido a los comentarios y al aumento del uso de las aplicaciones de Win32, hemos tomado la decisión de asignar previamente tres monitores virtuales durante el inicio de Windows Mixed Reality. Esto evita la interrupción y permite a los clientes iniciar hasta tres aplicaciones Win32 simultáneas sin tener que mostrar la inmovilización de los auriculares.

**Solución alternativa**

Desde entonces, hemos recibido comentarios de que algunos clientes, especialmente aquellos con varios monitores físicos, prefieren deshabilitar esta asignación previa del monitor virtual. Para ofrecer a los clientes el control, se ha habilitado una solución alternativa que implica cambiar el valor de una clave del registro, que está disponible con las siguientes actualizaciones de Windows:

- 2020-07 vista previa de actualización acumulativa para Windows 10, versión 2004 (KB4568831)
- 2020-10 vista previa de actualización acumulativa para Windows 10, versión 1909 (KB4580386)
- 2020-10 vista previa de actualización acumulativa para Windows 10, versión 1903 (KB4580386)

>[!NOTE]
>La modificación de los valores de clave del registro está destinada a usuarios avanzados.

>[!WARNING]
>La deshabilitación de la asignación previa del monitor virtual puede dar lugar a que se inmovilizan brevemente al iniciar una aplicación de Win32 (como vapor, el nuevo Microsoft Edge o Google Chrome) en Windows Mixed Reality.

Para deshabilitar la asignación previa del monitor virtual:
1. Compruebe **Windows Update** para una de las versiones de vista previa de las actualizaciones acumulativas de Windows 10 enumeradas anteriormente e instale la actualización cuando esté disponible. Puede encontrar la actualización en **actualizaciones opcionales** o **Opciones avanzadas** en la página Configuración de Windows Update
2. Iniciar el **Editor del registro**
3. Vaya a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si no está presente el REG_DWORD "PreallocateVirtualMonitors", créelo; para ello, seleccione **editar > nuevo > DWORD (32 bits)** y escriba PreallocateVirtualMonitors como nombre.
5. Si el REG_DWORD "PreallocateVirtualMonitors" está presente (o acaba de crearlo), haga doble clic en la entrada y cambie "datos del valor" de 1 (su valor predeterminado) a 0 (cero)
    * VERDADERO-1
    * FALSE: 0

Los monitores virtuales ahora se asignarán cuando intente iniciar una aplicación Win32 en Windows Mixed Reality en lugar de preasignarla. Para restablecer y volver a habilitar la asignación previa de los monitores virtuales, devuelva el valor DWORD "Data Value" a 1.

### <a name="other-known-issues"></a>Otros problemas conocidos

-   Los sitios web abiertos en Windows Mixed Reality se perderán cuando se cierre el portal de realidad mixta. Las ventanas de Microsoft Edge permanecerán en sus posiciones colocadas en la Página principal de la realidad mixta.
- Las experiencias de WebXR, incluida la extensión del visor 360, no se pueden iniciar correctamente en equipos con una configuración de GPU híbrida. Puede solucionar este problema habilitando una característica de vista previa en el nuevo Microsoft Edge. Vaya a `edge://flags` , busque "varias GPU" y habilite la marca llamada **compatibilidad con múltiples GPU de WebXR**.
-   El audio de las ventanas de Microsoft Edge no está espacial.
-   Se **corrigió en la versión de extensión de 360 Viewer 2.3.8**: abrir un vídeo de 360 desde YouTube en Windows Mixed Reality puede dar lugar a que el vídeo se distorsione en el casco. El reinicio de Edge debe actualizar de manera invisible la extensión del visor de 360 para resolver este problema. Puede confirmar qué versión de la extensión tiene escribiendo `edge://system/` en la barra de direcciones y seleccionando el botón de **expansión** junto a "extensiones".
