---
title: Errores de instalación
description: Solución Windows Mixed Reality de errores de instalación avanzada que va más allá de la documentación de soporte técnico al consumidor estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Installation
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213193"
---
# <a name="installation-errors"></a>Errores de instalación

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"El equipo no se puede ejecutar Windows Mixed Reality"

El equipo no cumple los [requisitos mínimos necesarios](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para ejecutar Windows Mixed Reality. Es posible que la configuración de hardware del equipo no sea compatible con Windows Mixed Reality, o es posible que deba actualizar a la versión más [reciente de Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

Windows Mixed Reality requiere un controlador de tarjeta gráfica que admita al menos WDDM 2.2. Asegúrese de que tiene la actualización más reciente del controlador del fabricante. Si Windows Mixed Reality configuración indica que la tarjeta gráfica no cumple los requisitos y cree que sí, asegúrese de que el casco está conectado a la tarjeta correcta.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Ya casi está allí: este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality"

El equipo no cumple los [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necesarios para la mejor experiencia en Windows Mixed Reality. Es posible que el equipo pueda ejecutar un casco envolvente, pero puede experimentar problemas de rendimiento y no poder ejecutar determinadas aplicaciones.

Windows Mixed Reality requiere un controlador de tarjeta gráfica que admita al menos WDDM 2.2. Asegúrese de que tiene la actualización más reciente del controlador del fabricante. Si Windows Mixed Reality configuración indica que la tarjeta gráfica no cumple los requisitos y cree que sí, asegúrese de que el casco está conectado a la tarjeta correcta.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Antes de poder configurar Windows Mixed Reality, el administrador deberá habilitarlo para su organización. Más información"

Probablemente se encuentra en una red administrada por la empresa y su organización usa Windows Server Update Services (WSUS). Estas y otras directivas que pueden bloquear la descarga. Póngase en contacto con el departamento de TI o el administrador del sistema de su organización para [habilitar Windows Mixed Reality](/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"No se pudo descargar el software de realidad mixta" o "Hang tight while we do some downloading" (No se pudo descargar el software de realidad mixta) o "Hang tight while we do some downloading" (No se pudo descargar el software de realidad mixta) o "Hang tight while we do some downloading" (No se pudo descargar el software de

* A veces, una actualización pendiente puede bloquear la descarga Mixed Reality Software. Vaya a **Configuración > Update & security > Windows Update** y asegúrese de que Windows update está en. A continuación, descargue e instale las actualizaciones en espera. Si recibe un error Windows actualización, obtenga ayuda [aquí.](https://support.microsoft.com/help/10164/fix-windows-update-errors)
* Asegúrese de que el equipo esté conectado a Internet y tenga al menos 2 GB de espacio de almacenamiento libre. Compruebe el estado de la red en: **Configuración > Network & Internet > Status**. Si no puede conectarse a Internet, obtenga ayuda [aquí.](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)  
* Reinicie el equipo e inténtelo de nuevo. 

Si estas soluciones no funcionan, pruebe lo siguiente:
* Si la Wi-Fi de red está establecida en [medida,](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)cámbiese a sin medir. Para desactivar una conexión de uso compartido, vaya a: **Configuración > Network & Internet > Status > Change connection properties > Set as metered connection** (Establecer como conexión de uso compartido) y seleccione "Desactivado".  
* Si ha instalado recientemente una actualización, puede causar problemas. No se recomienda quitar las actualizaciones instaladas, especialmente las actualizaciones de seguridad que mantienen el equipo seguro. Sin embargo, a veces quitar la actualización más reciente puede ayudar a determinar el origen del problema: 
    * Vaya a **Configuración > Update & Security > View Installed Update History (Historial de actualizaciones > actualizaciones de desinstalación).**
    * Seleccione la última actualización instalada y "Desinstalar".
    * Cuando se le pregunta "¿Está seguro, quiere desinstalar esta actualización?" responder "Sí". Si recibe un error al intentar estos pasos, obtenga más detalles sobre cómo corregir [errores de Windows Update.](https://support.microsoft.com//help/10164/fix-windows-update-errors) 
    * Reinicie el equipo e inténtelo de nuevo. 
    * Si Windows Mixed Reality se instala correctamente, vuelva **a** instalar las actualizaciones más recientes en Configuración > Windows Update > Check for Updates (Buscar actualizaciones) y compruebe si Windows Mixed Reality sigue funcionando. Si no se instala correctamente, vuelva a instalar las actualizaciones y póngase en contacto Windows soporte técnico. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Algo salió mal y no se pudo empezar a Windows Mixed Reality"
Para obtener más información sobre un código de error específico, vea [aquí](error-codes.md). También puede intentar:

* Desconecte ambos cables de casco del equipo.
* Reinicia el equipo.
* Vaya a **Configuración > Update & security > Windows Update** y asegúrese de que Windows update esté activado. Descargue e instale las actualizaciones en espera.
* Vuelva a conectar el casco al equipo y vuelva a intentar la configuración.

Si estos pasos no funcionan, desinstale y vuelva a instalar Windows Mixed Reality:
* Vaya a **Configuración > Mixed reality > Uninstall** (Desinstalar) y seleccione "Uninstall" (Desinstalar). 
* Reinicia tu equipo. 
* Para volver a iniciar el proceso de instalación, basta con conectar el casco al equipo.