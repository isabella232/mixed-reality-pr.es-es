---
title: Distribución de las aplicaciones
description: Información general de las diferentes opciones de distribución para distintas plataformas y almacenes de publicación compatibles.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: HoloLens, realidad mixta, auriculares envolventes, aplicación, UWP, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, Wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: f52109792e174a0b0fbdd9738539b5fc88f190a1
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443499"
---
# <a name="distributing-your-apps"></a>Distribución de las aplicaciones

![Lancher de aplicación 3D de pájaros de punto flotante en WMR Home](images/distribute-hero-image.png)

La obtención de las aplicaciones en manos de los usuarios o en el mundo es la más importante y a veces PAINSTAKING, parte de cualquier esfuerzo de desarrollo. Hemos simplificado el proceso en un conjunto de recursos que se enumeran a continuación, que dependen del escenario de distribución e implementación que mejor se adapte a usted o a su equipo.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opciones de distribución

> [!IMPORTANT]
> * Si va a compartir la aplicación con otra entidad, debe compilar y proporcionar el archivo appx. 
>     * Si usa el instalador de aplicaciones, también necesitará compartir el certificado con el usuario.
> 
> * Si está compartiendo con una organización, necesita una cuenta profesional o educativa y acceso a la infraestructura de [MDM (administración de dispositivos móviles)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) de las organizaciones.  
>    * Si es la entidad de uso compartido, debe ser administrador en el inquilino y usar el centro de [Administración de Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) para que la aplicación esté disponible. Otra opción es compartir el archivo appx y las dependencias de la aplicación con el usuario final.
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
    <td><strong>Instalación de dispositivo local</strong></td>
    <td><strong>Compartir con cualquier persona</strong></td>
    <td><strong>Compartir con una organización</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador de aplicaciones</strong></a> (a través de <a href="https://docs.microsoft.com/hololens/hololens-insider">compilaciones de Windows Insider</a>)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Portal de empresa MDM</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM: instalación de la aplicación requerida</strong></a></td>
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
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Paquete de aprovisionamiento</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#additional-scenarios"><strong>Implementación personalizada de Win32</strong></a> (solo Windows Mixed Reality; vea más abajo)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> El instalador de la aplicación no está disponible actualmente para dispositivos administrados o de HoloLens (primera generación).

## <a name="additional-scenarios"></a>Otros escenarios

* En el caso de la implementación de aplicaciones Win32, incluida la secuencia de vapor y la de juegos, puede generar un Win32. Archivo EXE que usa el destino de compilación independiente de PC de Unity y envíe las aplicaciones de la forma habitual a la plataforma elegida. 

* Si tiene que instalar una aplicación de HoloLens 2 mientras está sin conexión, consulte las instrucciones [seguras de hololens 2 sin conexión](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) o instale la aplicación a través de un paquete de aprovisionamiento sin habilitar el modo de desarrollador.

* También puede implementar compilaciones en el dispositivo y compartirlas con otros desarrolladores que tengan el modo de desarrollador habilitado mediante la [implementación y depuración con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o [la instalación de un paquete de aplicación con el portal de dispositivos](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).

## <a name="see-also"></a>Vea también
* [Buscar, instalar y desinstalar aplicaciones del Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->