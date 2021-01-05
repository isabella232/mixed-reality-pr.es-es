---
title: Errores de instalación
description: Solución avanzada de problemas de instalación de Windows Mixed Reality que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, instalación
appliesto:
- Windows 10
ms.openlocfilehash: 56ead28a5809eadef1797507168b68cbaf79953e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726066"
---
# <a name="installation-errors"></a>Errores de instalación

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"El equipo no puede ejecutar Windows Mixed Reality"

Su equipo no cumple los [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necesarios para ejecutar Windows Mixed Reality. Es posible que la configuración de hardware del equipo no sea compatible con Windows Mixed Reality, o que tenga que [actualizar a la versión más reciente de Windows](https://support.microsoft.com/help/12373/windows-update-faq). 

Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2. Asegúrese de que tiene la última actualización del controlador del fabricante. Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Ya está casi ahí: este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality"

Su equipo no cumple los [requisitos mínimos](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necesarios para la mejor experiencia en Windows Mixed Reality. Es posible que el equipo pueda ejecutar un casco envolvente, pero puede experimentar problemas de rendimiento y no poder ejecutar determinadas aplicaciones.

Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2. Asegúrese de que tiene la última actualización del controlador del fabricante. Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Antes de poder configurar Windows Mixed Reality, el administrador deberá habilitarlo para su organización. Más información "

Probablemente se encuentre en una red administrada por la empresa y su organización use Windows Server Update Services (WSUS). Estas y otras directivas pueden bloquear la descarga. Póngase en contacto con el administrador del sistema o el Departamento de TI de su organización para [habilitar Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"No pudimos descargar el software de realidad mixta" ni "colgar mientras hacemos una descarga"

* A veces, una actualización pendiente puede bloquear la descarga de software de realidad mixta. Vaya a **configuración > actualizar & security > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones en espera. Si recibe un error de Windows Update, obtenga ayuda [aquí](https://support.microsoft.com/help/10164/fix-windows-update-errors).
* Asegúrese de que el equipo está conectado a Internet y tiene al menos 2 GB de espacio de almacenamiento libre. Compruebe el estado de la red en: **configuración > red & estado de > de Internet**. Si no puede conectarse a Internet, obtenga ayuda [aquí](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues).  
* Reinicie el equipo e inténtelo de nuevo. 

Si estas soluciones no funcionan, pruebe lo siguiente:
* Si la conexión de red Wi-Fi está establecida en [medido](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq), cámbiela a desmedido. Para desactivar una conexión de uso medido, vaya a: **configuración > red & Internet > estado > cambiar las propiedades de conexión > establecer como conexión de uso medido** y seleccione "desactivado".  
* Si ha instalado recientemente una actualización, puede causar problemas. No se recomienda quitar las actualizaciones instaladas, especialmente las actualizaciones de seguridad que mantienen el equipo seguro. Sin embargo, a veces quitar la actualización más reciente puede ayudar a determinar el origen del problema: 
    * Vaya a **configuración > actualizar & seguridad > ver el historial de actualizaciones instaladas > desinstalar actualizaciones**
    * Seleccione la última actualización instalada y "desinstalar".
    * Cuando se le pregunte ¿está seguro de que desea desinstalar esta actualización? " responda "sí". Si recibe un error al intentar realizar estos pasos, obtenga más información sobre cómo corregir los [errores de Windows Update](https://support.microsoft.com//help/10164/fix-windows-update-errors). 
    * Reinicie el equipo e inténtelo de nuevo. 
    * Si Windows Mixed Reality se instala correctamente, vuelva a instalar las actualizaciones más recientes en **configuración > Windows Update > comprobar si hay actualizaciones** y ver si Windows Mixed Reality continúa funcionando. Si no se instala correctamente, vuelva a instalar las actualizaciones y póngase en contacto con el soporte técnico de Windows. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Se produjo un error y no se pudo iniciar Windows Mixed Reality"
Para obtener más información sobre un código de error específico, mire [aquí](error-codes.md). También puede intentar:

* Desconecte ambos cables de auriculares del equipo.
* Reinicia el equipo.
* Vaya a **configuración > actualizar & seguridad > Windows Update** y asegúrese de que Windows Update está activado. Descargue e instale las actualizaciones en espera.
* Vuelva a conectar los auriculares al equipo y, a continuación, intente realizar de nuevo la instalación.

Si estos pasos no funcionan, desinstale y vuelva a instalar Windows Mixed Reality:
* Vaya a **configuración > realidad mixta > desinstalar** y seleccione "desinstalar". 
* Reinicia tu equipo. 
* Para volver a iniciar el proceso de instalación, simplemente conecte el casco a su PC.
