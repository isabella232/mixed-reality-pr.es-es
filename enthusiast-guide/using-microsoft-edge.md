---
title: Uso Microsoft Edge en Windows Mixed Reality
description: Prepárese para la nueva Microsoft Edge en Windows Mixed Reality. Incluye los cambios esperados, las actualizaciones que hay que buscar y los problemas conocidos.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Navigate, Get around, apps, games, Microsoft Edge, chromium, Edge, 360, 360 video, 360 viewer
ms.openlocfilehash: 3cdb051e9925338a5f0145e106e2213712eb611e575b9f5d7dd29342a52ff38d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199491"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality y la nueva Microsoft Edge

La [nueva Microsoft Edge](https://www.microsoft.com/edge) está disponible para su descarga y ha empezado a implementarse automáticamente para los clientes a través de Windows Update. 

La nueva Microsoft Edge [adopta el Chromium de código abierto](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) en el escritorio. Esto crea una mejor compatibilidad para los clientes y menos fragmentación para los desarrolladores web. También admitirá WebXR en el lanzamiento, que es el nuevo estándar para crear experiencias web envolventes para cascos vr, en lugar de WebVR.

>[!IMPORTANT]
>Al instalar Microsoft Edge en un dispositivo Windows 10 actualizado, reemplazará la versión anterior (heredada) en el equipo.

## <a name="installing-the-new-microsoft-edge"></a>Instalación de la nueva Microsoft Edge 

Antes de instalar el nuevo Microsoft Edge, actualice **a Windows 10 versión 1903** o posterior para obtener compatibilidad con aplicaciones Win32 nativas, como el nuevo Microsoft Edge en Windows Mixed Reality. Compruebe Windows actualizar o [instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/software-download/windows10).

Una vez que Windows 10 versión 1903 o posterior, estará listo para el nuevo Microsoft Edge. La nueva Microsoft Edge se está implementando a través de Windows Update, pero puede instalar manualmente el nuevo Microsoft Edge desde el sitio web de [Microsoft Edge](https://www.microsoft.com/edge) si lo desea antes.

>[!IMPORTANT]
>La nueva Microsoft Edge se inicia con compatibilidad con WebXR, el nuevo estándar para crear experiencias web envolventes para cascos vr. Al instalar el nuevo Microsoft Edge, ya no podrá reproducir experiencias webVR en Microsoft Edge. 

## <a name="known-issues"></a>Problemas conocidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10 versión 1903 (o posterior)

- El inicio de cualquier aplicación Win32, incluida la nueva Microsoft Edge, hace que la pantalla del casco se congele brevemente.
- El Microsoft Edge de datos desaparece del Windows Mixed Reality menú Inicio (puede encontrarlo en la carpeta "Aplicaciones clásicas").
- Windows de la versión Microsoft Edge se siguen colocando alrededor del ambiente principal, pero no se pueden usar. Al intentar activar esas ventanas, se inicia Edge en la aplicación de escritorio.
- Al seleccionar un hipervínculo en el ambiente principal se inicia un explorador web en el escritorio en lugar del ambiente principal.
- La aplicación WebVR Showcase está presente en el ambiente principal, a pesar de que Ya no se admite WebVR.
- Mejoras generales en el inicio del teclado y los objetos visuales.

### <a name="monitor-and-input-handling-issues"></a>Supervisión y problemas de control de entrada

Después de realizar la actualización acumulativa 2020-01 para Windows 10 versión 1903 o posterior, los monitores virtuales aparecerán como monitores físicos genéricos en Configuración > **System > Display** durante Windows Mixed Reality sesiones. Algunos clientes, especialmente aquellos con más de un monitor físico, pueden observar problemas con el diseño de escritorio y el control de entradas como resultado.

**¿Por qué ocurre esto?**

La compatibilidad con las aplicaciones Win32 clásicas Windows Mixed Reality se introdujo con [el Actualización de mayo de 2019 de Windows 10](/windows/mixed-reality/release-notes-may-2019). Para habilitar esta compatibilidad, se debe crear un monitor virtual para hospedar la aplicación Win32. Cada vez que se inicia una nueva aplicación Win32, se debe crear otro monitor virtual. Desafortunadamente, la creación de un monitor virtual es una tarea intensiva que puede hacer que la pantalla del casco se congele brevemente. Los clientes proporcionaron comentarios que desconocciones y interrupciones en la experiencia. Debido a ese comentario, junto con el aumento del uso de aplicaciones Win32, decidimos asignar previamente tres monitores virtuales durante el inicio de Windows Mixed Reality para evitar esta interrupción y permitir que los clientes inicien hasta tres aplicaciones Win32 simultáneas sin experimentar la inmovilización de la pantalla del casco.

**Solución alternativa**

Desde entonces hemos recibido comentarios que algunos clientes, especialmente los que tienen varios monitores físicos, prefieren deshabilitar la asignación previa de este monitor virtual. Para proporcionar a los clientes más control, hemos habilitado una solución alternativa que implica cambiar un valor de clave del Registro, disponible con las siguientes Windows actualizaciones:

- Versión preliminar de actualización acumulativa 2020-07 para Windows 10 versión 2004 (KB4568831)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1909 (KB4580386)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1903 (KB4580386)

>[!NOTE]
>La modificación de valores de clave del Registro está pensada para usuarios avanzados.

>[!WARNING]
>La deshabilitación de la asignación previa del monitor virtual puede provocar que la pantalla del casco se congele brevemente al iniciar una aplicación Win32 (como Steam, el nuevo Microsoft Edge o Google Chrome) en Windows Mixed Reality.

Para deshabilitar la asignación previa del monitor virtual:
1. Compruebe **Windows actualización para obtener** una de las versiones preliminares de Windows 10 acumulativas enumeradas anteriormente e instale la actualización cuando esté disponible. Puede encontrar la actualización en **Actualizaciones** opcionales o Opciones **avanzadas en** la Windows configuración de actualización.
2. Iniciar **el Editor del Registro**
3. Vaya a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si el REG_DWORD "PreallocateVirtualMonitors" no está presente, para crearlo, seleccione Editar > nuevo **> valor DWORD (32 bits)** y escriba PreallocateVirtualMonitors como nombre.
5. Si el REG_DWORD "PreallocateVirtualMonitors" está presente (o acaba de crearlo), haga doble clic en la entrada y cambie "Datos de valor" de 1 (su valor predeterminado) a 0 (cero)
    * TRUE - 1
    * FALSE - 0

Los monitores virtuales ahora se asignarán cuando intente iniciar una aplicación Win32 en Windows Mixed Reality en lugar de asignar previamente. Para restablecer esta asignación y volver a habilitar la asignación previa del monitor virtual, devuelva el valor DWORD "Datos de valor" a 1.

### <a name="other-known-issues"></a>Otros problemas conocidos

-   Los sitios web abiertos Windows Mixed Reality se perderán cuando Portal de realidad mixta cierre, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en el ambiente principal.
- Es posible que las experiencias de WebXR, incluida la extensión 360 Viewer, no se inicien correctamente en equipos con una configuración de GPU híbrida. Puede evitar este problema habilitando una característica en versión preliminar en el nuevo Microsoft Edge. Vaya a `edge://flags` , busque "multi gpu" y habilite la marca denominada Compatibilidad con Multi GPU de **WebXR.**
-   El audio Microsoft Edge ventanas no está espacializado.
-   Se corrigió en la versión **2.3.8** de la extensión 360 Viewer: la apertura de un vídeo 360 desde YouTube en Windows Mixed Reality puede provocar que el vídeo esté distorsionado en el casco. Reiniciar Edge debe actualizar invisiblemente la extensión 360 Viewer para resolver este problema. Para confirmar qué versión de la extensión tiene, escriba en la barra de direcciones y seleccione el botón Expandir situado junto `edge://system/` a "Extensiones". 