---
title: Windows Mixed Reality y la nueva Microsoft Edge
description: Obtenga información sobre las nuevas Microsoft Edge para Mixed Reality, incluido lo que se espera, las actualizaciones que hay que buscar y los problemas conocidos.
author: mattzmsft
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: ca849f63d2a755639bedba68c47e419528006a6d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148665"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>La nueva Microsoft Edge para Windows Mixed Reality

El nuevo Microsoft Edge ya está disponible para su [descarga,](https://blogs.windows.com/windowsexperience/?p=173496)pero los clientes también pueden esperar a que una actualización futura la instale con [Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), siguiendo un enfoque de implementación medido durante los próximos meses. 

Con estas noticias, queríamos que los clientes de cascos de realidad virtual de Windows Mixed Reality sepan qué esperar de la nueva Microsoft Edge y mostrar las actualizaciones pendientes para una experiencia de exploración mejorada **en Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Presentación de la nueva versión de Microsoft Edge

El nuevo Microsoft Edge adopta el proyecto de código abierto Chromium en el escritorio para crear una mejor compatibilidad para los clientes y una menor fragmentación de la web [para](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) desarrolladores web. También admitirá WebXR en el lanzamiento, el nuevo estándar para crear experiencias web envolventes para cascos vr, en lugar de WebVR.

>[!IMPORTANT]
>Al instalar Microsoft Edge en un dispositivo Windows 10 actualizado, reemplazará la versión anterior (heredada) en el equipo.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Prepararse para la nueva Microsoft Edge

Windows Mixed Reality Los clientes de cascos de realidad virtual que quieran usar el nuevo Microsoft Edge en ambiente principal deben actualizar Windows 10 la versión **1903** o posterior para la compatibilidad nativa de aplicaciones Win32 (como la nueva Microsoft Edge) en el ambiente principal. Compruebe Windows actualizar o [instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Para obtener la mejor experiencia Microsoft Edge posible en ambiente principal, también se recomienda esperar algunas optimizaciones clave de Windows Mixed Reality para el nuevo Microsoft Edge que llega con la actualización acumulativa **2020-01 para la versión 1903 de Windows 10 (o posterior),** que debe estar disponible en Windows Update a finales de enero.

>[!IMPORTANT]
>Si opta por descargar el nuevo Microsoft Edge antes de realizar estas actualizaciones, habrá algunos problemas conocidos con su comportamiento en Windows Mixed Reality (que puede leer a continuación).

## <a name="known-issues"></a>Problemas conocidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10 versión 1903 (o posterior)

- El inicio de cualquier aplicación Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se congele brevemente.
- El Microsoft Edge desaparece de la Windows Mixed Reality menú Inicio (puede encontrarlo en la carpeta "Aplicaciones clásicas").
- Windows de la versión Microsoft Edge se siguen colocando alrededor del ambiente principal, pero no se pueden usar. Al intentar activar esas ventanas, edge se inicia en la aplicación de escritorio.
- Al seleccionar un hipervínculo en el ambiente principal se inicia un explorador web en el escritorio en lugar del ambiente principal.
- La aplicación Presentación de WebVR está presente en el ambiente principal, a pesar de que ya no se admite WebVR.
- Mejoras generales en los objetos visuales y el inicio del teclado.

### <a name="monitor-and-input-handling-issues"></a>Supervisión y control de entrada de problemas

Después de realizar la actualización acumulativa 2020-01 para la versión 1903 de Windows 10 (o posterior), los monitores virtuales aparecerán como monitores físicos genéricos en Configuración > **System > Display** durante Windows Mixed Reality sesiones. Algunos clientes, especialmente con más de un monitor físico, pueden observar problemas con el diseño de escritorio y el control de entradas como resultado.

**Por qué ocurre esto**

La compatibilidad con las aplicaciones win32 clásicas Windows Mixed Reality se introdujo con [el Actualización de mayo de 2019 de Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019). Para habilitar esta compatibilidad, se debe crear un monitor virtual para hospedar la aplicación Win32. Cada vez que se inicia una nueva aplicación Win32, se debe crear otro monitor virtual. Desafortunadamente, la creación de un monitor virtual es una tarea intensiva que puede hacer que la pantalla del casco se congele brevemente. Los clientes han ofrecido comentarios que den cuenta de que se trata de una experiencia poco cómoda y perjudicial. Debido a los comentarios y al aumento del uso de la aplicación Win32, hemos tomado la decisión de asignar previamente tres monitores virtuales durante el inicio de Windows Mixed Reality. Esto evita la interrupción y permite a los clientes iniciar hasta tres aplicaciones Win32 simultáneas sin experimentar la inmovilización de la pantalla del casco.

**Solución alternativa**

Desde entonces hemos recibido comentarios de que algunos clientes, especialmente los que tienen varios monitores físicos, prefieren deshabilitar la asignación previa de este monitor virtual. Para proporcionar a los clientes el control, hemos habilitado una solución alternativa que implica cambiar un valor de clave del Registro, que está disponible con las siguientes Windows actualizaciones:

- Versión preliminar de actualización acumulativa 2020-07 para Windows 10 versión 2004 (KB4568831)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1909 (KB4580386)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1903 (KB4580386)

>[!NOTE]
>La modificación de los valores de clave del Registro está pensada para usuarios avanzados.

>[!WARNING]
>Deshabilitar la asignación previa del monitor virtual puede provocar que la pantalla del casco se bloquee brevemente al iniciar una aplicación Win32 (como Steam, el nuevo Microsoft Edge o Google Chrome) en Windows Mixed Reality.

Para deshabilitar la asignación previa del monitor virtual:
1. Compruebe **Windows actualización de una** de las Windows 10 versión preliminar de la actualización acumulativa enumeradas anteriormente e instale la actualización cuando esté disponible. Puede encontrar la actualización en Actualizaciones **opcionales o** **Opciones avanzadas en** la Windows configuración de actualización.
2. Iniciar **el Editor del Registro**
3. Vaya a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si el REG_DWORD "PreallocateVirtualMonitors" no está presente, para crearlo, seleccione Editar > > Nuevo valor **DWORD (32 bits)** y escriba PreallocateVirtualMonitors como nombre.
5. Si el REG_DWORD "PreallocateVirtualMonitors" está presente (o acaba de crearlo), haga doble clic en la entrada y cambie "Datos de valor" de 1 (su valor predeterminado) a 0 (cero)
    * TRUE : 1
    * FALSE - 0

Los monitores virtuales ahora se asignarán cuando intente iniciar una aplicación Win32 en Windows Mixed Reality en lugar de asignar previamente. Para restablecer esta asignación y volver a habilitar la asignación previa del monitor virtual, devuelva el valor DWORD "Datos de valor" a 1.

### <a name="other-known-issues"></a>Otros problemas conocidos

-   El audio Microsoft Edge ventanas no está espacializado.

## <a name="see-also"></a>Consulte también

* [Información general sobre WebXR](../develop/javascript/webxr-overview.md)