---
title: Distribución de las aplicaciones
description: Información general de las distintas opciones de distribución para varias plataformas admitidas y almacenes de publicación.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, cascos envolventes, aplicación, uwp, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, wack, certificación, paquete, appx, merchandising
ms.openlocfilehash: 7d4fbc1a7a5767ad8276017c7cdc38e9bb436bc83b12a4d8caeb9a8d84f1caca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198794"
---
# <a name="distributing-your-apps"></a>Distribución de las aplicaciones

![Floaty bird 3D app lancher in WMR home](images/distribute-hero-image.png)

Poner las aplicaciones en manos de los usuarios o en el mundo es la parte más importante, y a veces difícil, de cualquier esfuerzo de desarrollo. Hemos simplificado el proceso en un conjunto de recursos, que dependen del escenario de distribución e implementación más adecuado para usted o su equipo.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opciones de distribución

> [!IMPORTANT]
> * Si comparte la aplicación con otra parte, debe compilar y proporcionar el archivo appx. 
>     * Si usa Instalador de aplicación, también deberá compartir el certificado con el usuario.
> 
> * Si va a compartir con una organización, necesita una cuenta profesionales o educativas y acceso a la infraestructura [de MDM (Mobile Administración de dispositivos)](/hololens/hololens-enroll-mdm) de las organizaciones.  
>    * Si es la entidad de uso compartido, debe ser administrador [](/mem/intune/apps/apps-deploy) en el inquilino y usar el centro de administración de Microsoft Endpoint Manager para que la aplicación esté disponible. Otra opción es compartir el archivo appx y las dependencias de la aplicación con el usuario final.
>    * Si es el usuario final, la aplicación se descargará automáticamente o estará disponible para su descarga una vez que se inscriba en el inquilino de la organización de uso compartido. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Escenario</strong></td>
    <td><strong>Instalación de dispositivos locales</strong></td>
    <td><strong>Compartir con cualquier persona</strong></td>
    <td><strong>Compartir con una organización</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador de aplicación</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM: Portal de empresa</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM: instalación de aplicación necesaria</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>Paquete de aprovisionamiento</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Implementación personalizada de Win32</strong></a> (no disponible para dispositivos HoloLens personalizados ( consulte a continuación)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Instalador de aplicación no está disponible actualmente para dispositivos administrados o HoloLens (1.ª generación).

## <a name="other-scenarios"></a>Otros escenarios

* Puede generar un archivo de .EXE Win32 mediante el destino de compilación independiente del equipo desde Unity para la implementación de aplicaciones Win32, incluidos Steam y Game Pass. Una vez que tenga la .EXE, puede enviar las aplicaciones de la forma habitual a la plataforma elegida. 

* Si necesita instalar una aplicación HoloLens 2 mientras está sin conexión, [](/hololens/hololens-common-scenarios-offline-secure) consulte las instrucciones de HoloLens 2 seguras sin conexión o instale la aplicación a través de un paquete de aprovisionamiento sin habilitar el modo de desarrollador.

* También puede implementar compilaciones en el dispositivo y compartirlas con otros desarrolladores que tengan habilitado el modo de desarrollador mediante la implementación y [depuración](../develop/platform-capabilities-and-apis/using-visual-studio.md) con Visual Studio o la instalación de un paquete de [aplicación con el Portal de dispositivos](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Consulte también
* [Búsqueda, instalación y desinstalación de aplicaciones de la Microsoft Store](/hololens/holographic-store-apps)