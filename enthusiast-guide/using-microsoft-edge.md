---
title: Uso Microsoft Edge en Windows Mixed Reality
description: Prepárese para la nueva Microsoft Edge en Windows Mixed Reality. Incluye los cambios esperados, las actualizaciones que hay que buscar y los problemas conocidos.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Navigate, Get around, apps, games, Microsoft Edge, chromium, Edge, 360, 360 video, 360 viewer
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436705"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality y el nuevo Microsoft Edge

El [nuevo Microsoft Edge](https://www.microsoft.com/edge) está disponible para su descarga y ha empezado a implementarse automáticamente para los clientes a través de Windows Update. 

El nuevo Microsoft Edge [adopta el Chromium de código abierto en](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) el escritorio. Esto crea una mejor compatibilidad para los clientes y menos fragmentación para los desarrolladores web. También admitirá WebXR en el lanzamiento, que es el nuevo estándar para crear experiencias web envolventes para cascos vr, en lugar de WebVR.

>[!IMPORTANT]
>Al instalar Microsoft Edge en un dispositivo Windows 10 o Windows 11 actualizado, reemplazará la versión anterior (heredada) en el equipo.

## <a name="installing-the-new-microsoft-edge"></a>Instalación del nuevo Microsoft Edge 

Antes de instalar el nuevo Microsoft Edge, actualice Windows 10 la versión **1903** o posterior o Windows 11 para la compatibilidad con aplicaciones win32 nativas, como el nuevo Microsoft Edge en Windows Mixed Reality. Compruebe Windows actualizar o [instalar manualmente](https://www.microsoft.com/software-download/windows10) la versión más reciente de Windows 10 o Windows 11.

Una vez que Windows 10 versión 1903 o posterior o Windows 11, estará listo para el nuevo Microsoft Edge. El nuevo Microsoft Edge se está implementando a través de Windows Update, pero puede instalar manualmente el nuevo Microsoft Edge desde el sitio web de [Microsoft Edge](https://www.microsoft.com/edge) si lo desea antes.

>[!IMPORTANT]
>La nueva Microsoft Edge se inicia con compatibilidad con WebXR, el nuevo estándar para crear experiencias web envolventes para cascos vr. Al instalar el nuevo Microsoft Edge, ya no podrá reproducir experiencias de WebVR en Microsoft Edge. 

## <a name="known-issues"></a>Problemas conocidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10 versión 1903 (o posterior)

- El inicio de cualquier aplicación Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se congele brevemente.
- El Microsoft Edge desaparece de la Windows Mixed Reality menú Inicio (puede encontrarlo en la carpeta "Aplicaciones clásicas").
- Windows del Microsoft Edge se siguen colocando alrededor del ambiente principal, pero no se pueden usar. Al intentar activar esas ventanas, edge se inicia en la aplicación de escritorio.
- Al seleccionar un hipervínculo en el ambiente principal se inicia un explorador web en el escritorio en lugar del ambiente principal.
- La aplicación Presentación de WebVR está presente en el ambiente principal, a pesar de que ya no se admite WebVR.
- Mejoras generales en los objetos visuales y el inicio del teclado.

### <a name="monitor-and-input-handling-issues"></a>Supervisión y control de entrada de problemas

Después de realizar la actualización acumulativa 2020-01 para la versión 1903 de Windows 10 o posterior, los monitores virtuales aparecerán como monitores físicos genéricos en Configuración > **System > Display** durante Windows Mixed Reality sesiones. Algunos clientes, especialmente los que tienen más de un monitor físico, pueden observar problemas con el diseño de escritorio y el control de entradas como resultado.

**Por qué ocurre esto**

La compatibilidad con las aplicaciones win32 clásicas Windows Mixed Reality se introdujo con [el Actualización de mayo de 2019 de Windows 10](/windows/mixed-reality/release-notes-may-2019). Para habilitar esta compatibilidad, se debe crear un monitor virtual para hospedar la aplicación Win32. Cada vez que se inicia una nueva aplicación Win32, se debe crear otro monitor virtual. Desafortunadamente, la creación de un monitor virtual es una tarea intensiva que puede hacer que la pantalla del casco se congele brevemente. Los clientes han ofrecido comentarios que den cuenta de que la experiencia no era incomod y perjudicial. Debido a estos comentarios, junto con el aumento del uso de aplicaciones Win32, decidimos asignar previamente tres monitores virtuales durante el inicio de Windows Mixed Reality para evitar esta interrupción y permitir que los clientes inicien hasta tres aplicaciones Win32 simultáneas sin experimentar la inmovilización de la pantalla del casco.

**Solución alternativa**

Desde entonces, hemos recibido comentarios que algunos clientes, especialmente los que tienen varios monitores físicos, prefieren deshabilitar la asignación previa de este monitor virtual. Para proporcionar a los clientes más control, hemos habilitado una solución alternativa que implica cambiar un valor de clave del Registro, disponible con las siguientes Windows Actualizaciones:

- Versión preliminar de actualización acumulativa 2020-07 para Windows 10 versión 2004 (KB4568831)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1909 (KB4580386)
- Versión preliminar de actualización acumulativa 2020-10 Windows 10 versión 1903 (KB4580386)

>[!NOTE]
>La modificación de los valores de clave del Registro está pensada para usuarios avanzados.

>[!WARNING]
>Deshabilitar la asignación previa del monitor virtual puede provocar que la pantalla del casco se bloquee brevemente al iniciar una aplicación Win32 (como Steam, el nuevo Microsoft Edge o Google Chrome) en Windows Mixed Reality.

Para deshabilitar la asignación previa del monitor virtual:
1. Compruebe **Windows actualización de una** de las Windows 10 versión preliminar de actualización acumulativa enumeradas anteriormente e instale la actualización cuando esté disponible. Puede encontrar la actualización en Actualizaciones **opcionales o** **Opciones avanzadas en** la Windows configuración de actualización.
2. Iniciar **el Editor del Registro**
3. Vaya a "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Si el REG_DWORD "PreallocateVirtualMonitors" no está presente, para crearlo, seleccione Editar > > nuevo valor **DWORD (32 bits)** y escriba PreallocateVirtualMonitors como nombre.
5. Si el REG_DWORD "PreallocateVirtualMonitors" está presente (o acaba de crearlo), haga doble clic en la entrada y cambie "Datos de valor" de 1 (su valor predeterminado) a 0 (cero)
    * TRUE : 1
    * FALSE - 0

Los monitores virtuales ahora se asignarán cuando intente iniciar una aplicación Win32 en Windows Mixed Reality en lugar de asignar previamente. Para restablecer esta asignación y volver a habilitar la asignación previa del monitor virtual, devuelva el valor DWORD "Datos de valor" a 1.

### <a name="other-known-issues"></a>Otros problemas conocidos

-   Los sitios web abiertos Windows Mixed Reality se perderán cuando Portal de realidad mixta cierre, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en el ambiente principal.
- Es posible que las experiencias de WebXR, incluida la extensión visor 360, no se inicien correctamente en equipos con una configuración de GPU híbrida. Puede evitar este problema habilitando una característica en versión preliminar en el nuevo Microsoft Edge. Vaya a , busque "multi gpu" y habilite la marca denominada Compatibilidad con `edge://flags` **Multi GPU de WebXR.**
-   El audio Microsoft Edge ventanas no está espacializado.
-   Corregido en **la versión 2.3.8** de la extensión 360 Viewer: la apertura de un vídeo 360 desde YouTube en Windows Mixed Reality puede provocar que el vídeo se desvirtue en el casco. Reiniciar Edge debe actualizar invisiblemente la extensión 360 Viewer para resolver este problema. Para confirmar qué versión de la extensión tiene, escriba en la barra de direcciones y seleccione el botón Expandir situado `edge://system/` junto a  "extensiones".