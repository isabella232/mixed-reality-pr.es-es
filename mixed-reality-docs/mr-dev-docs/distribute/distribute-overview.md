---
title: Distribución de las aplicaciones
description: Información general de las diferentes opciones de distribución para distintas plataformas y almacenes de publicación compatibles.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realidad mixta, auriculares envolventes, aplicación, UWP, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, Wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: eb06ff46be6fbe6e480f9b43fa7f23ee47982192
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582850"
---
# <a name="distributing-your-apps"></a>Distribución de las aplicaciones

![Lancher de aplicación 3D de pájaros de punto flotante en WMR Home](images/distribute-hero-image.png)

La obtención de las aplicaciones en manos de los usuarios o en el mundo es la más importante y a veces PAINSTAKING, parte de cualquier esfuerzo de desarrollo. Hemos simplificado el proceso en un conjunto de recursos, que dependen del escenario de distribución e implementación que mejor se adapte a usted o a su equipo.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opciones de distribución

> [!IMPORTANT]
> * Si va a compartir la aplicación con otra entidad, debe compilar y proporcionar el archivo appx. 
>     * Si usa el instalador de aplicaciones, también necesitará compartir el certificado con el usuario.
> 
> * Si está compartiendo con una organización, necesita una cuenta profesional o educativa y acceso a la infraestructura de [MDM (administración de dispositivos móviles)](/hololens/hololens-enroll-mdm) de las organizaciones.  
>    * Si es la entidad de uso compartido, debe ser administrador en el inquilino y usar el centro de [Administración de Microsoft Endpoint Manager](/mem/intune/apps/apps-deploy) para que la aplicación esté disponible. Otra opción es compartir el archivo appx y las dependencias de la aplicación con el usuario final.
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
    <td><strong>Instalaciones de dispositivos locales</strong></td>
    <td><strong>Compartir con cualquier persona</strong></td>
    <td><strong>Compartir con una organización</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador de la aplicación</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>Portal de empresa MDM</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM: instalación de la aplicación requerida</strong></a></td>
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
    <td><a href="#other-scenarios"><strong>Implementación personalizada de Win32</strong></a> (no está disponible para dispositivos HoloLens; consulte a continuación).</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> El instalador de la aplicación no está disponible actualmente para dispositivos administrados o de HoloLens (primera generación).

## <a name="other-scenarios"></a>Otros escenarios

* Puede generar un Win32. Archivo EXE que usa el destino de compilación independiente de PC de Unity para la implementación de aplicaciones de Win32, incluido el paso de juegos y vapor. Una vez que tenga. EXE, puede enviar sus aplicaciones de la forma habitual a la plataforma elegida. 

* Si tiene que instalar una aplicación de HoloLens 2 mientras está sin conexión, consulte las instrucciones [seguras de hololens 2 sin conexión](/hololens/hololens-common-scenarios-offline-secure) o instale la aplicación a través de un paquete de aprovisionamiento sin habilitar el modo de desarrollador.

* También puede implementar compilaciones en el dispositivo y compartirlas con otros desarrolladores que tengan el modo de desarrollador habilitado mediante la [implementación y depuración con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o [la instalación de un paquete de aplicación con el portal de dispositivos](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Consulte también
* [Buscar, instalar y desinstalar aplicaciones del Microsoft Store](/hololens/holographic-store-apps)