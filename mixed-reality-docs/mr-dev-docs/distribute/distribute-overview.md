---
title: Distribución de las aplicaciones
description: Información general de las diferentes opciones de distribución para distintas plataformas y almacenes de publicación compatibles.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realidad mixta, auriculares envolventes, aplicación, UWP, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, Wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215980"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="ce6e4-104">Distribución de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="ce6e4-104">Distributing your apps</span></span>

![Lancher de aplicación 3D de pájaros de punto flotante en WMR Home](images/distribute-hero-image.png)

<span data-ttu-id="ce6e4-106">La obtención de las aplicaciones en manos de los usuarios o en el mundo es la más importante y a veces PAINSTAKING, parte de cualquier esfuerzo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="ce6e4-107">Hemos simplificado el proceso en un conjunto de recursos, que dependen del escenario de distribución e implementación que mejor se adapte a usted o a su equipo.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="ce6e4-108">Opciones de distribución</span><span class="sxs-lookup"><span data-stu-id="ce6e4-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="ce6e4-109">Si va a compartir la aplicación con otra entidad, debe compilar y proporcionar el archivo appx.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="ce6e4-110">Si usa el instalador de aplicaciones, también necesitará compartir el certificado con el usuario.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="ce6e4-111">Si está compartiendo con una organización, necesita una cuenta profesional o educativa y acceso a la infraestructura de [MDM (administración de dispositivos móviles)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) de las organizaciones.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="ce6e4-112">Si es la entidad de uso compartido, debe ser administrador en el inquilino y usar el centro de [Administración de Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) para que la aplicación esté disponible.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="ce6e4-113">Otra opción es compartir el archivo appx y las dependencias de la aplicación con el usuario final.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="ce6e4-114">Si es el usuario final, la aplicación se descargará automáticamente o estará disponible para su descarga una vez que se inscriba en el inquilino de la organización de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="ce6e4-115"><strong>Escenario</strong></span><span class="sxs-lookup"><span data-stu-id="ce6e4-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="ce6e4-116"><strong>Instalaciones de dispositivos locales</strong></span><span class="sxs-lookup"><span data-stu-id="ce6e4-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="ce6e4-117"><strong>Compartir con cualquier persona</strong></span><span class="sxs-lookup"><span data-stu-id="ce6e4-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="ce6e4-118"><strong>Compartir con una organización</strong></span><span class="sxs-lookup"><span data-stu-id="ce6e4-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador de la aplicación</strong></span><span class="sxs-lookup"><span data-stu-id="ce6e4-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="ce6e4-120">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-120">✔️</span></span></td>
    <td><span data-ttu-id="ce6e4-121">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Portal de empresa MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce6e4-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="ce6e4-123">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM: instalación de la aplicación requerida</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce6e4-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="ce6e4-125">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce6e4-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="ce6e4-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-127">✔️</span></span></td>
    <td><span data-ttu-id="ce6e4-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce6e4-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="ce6e4-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Paquete de aprovisionamiento</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce6e4-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="ce6e4-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-132">✔️</span></span></td>
    <td><span data-ttu-id="ce6e4-133">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-133">✔️</span></span></td>
    <td><span data-ttu-id="ce6e4-134">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="ce6e4-135"><a href="#other-scenarios"><strong>Implementación personalizada de Win32</strong></a> (no está disponible para dispositivos HoloLens; consulte a continuación).</span><span class="sxs-lookup"><span data-stu-id="ce6e4-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="ce6e4-136">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-136">✔️</span></span></td>
    <td><span data-ttu-id="ce6e4-137">✔️</span><span class="sxs-lookup"><span data-stu-id="ce6e4-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="ce6e4-138">El instalador de la aplicación no está disponible actualmente para dispositivos administrados o de HoloLens (primera generación).</span><span class="sxs-lookup"><span data-stu-id="ce6e4-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="ce6e4-139">Otros escenarios</span><span class="sxs-lookup"><span data-stu-id="ce6e4-139">Other scenarios</span></span>

* <span data-ttu-id="ce6e4-140">Puede generar un Win32. Archivo EXE que usa el destino de compilación independiente de PC de Unity para la implementación de aplicaciones de Win32, incluido el paso de juegos y vapor.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="ce6e4-141">Una vez que tenga. EXE, puede enviar sus aplicaciones de la forma habitual a la plataforma elegida.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="ce6e4-142">Si tiene que instalar una aplicación de HoloLens 2 mientras está sin conexión, consulte las instrucciones [seguras de hololens 2 sin conexión](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) o instale la aplicación a través de un paquete de aprovisionamiento sin habilitar el modo de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="ce6e4-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="ce6e4-143">También puede implementar compilaciones en el dispositivo y compartirlas con otros desarrolladores que tengan el modo de desarrollador habilitado mediante la [implementación y depuración con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o [la instalación de un paquete de aplicación con el portal de dispositivos](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span><span class="sxs-lookup"><span data-stu-id="ce6e4-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce6e4-144">Vea también</span><span class="sxs-lookup"><span data-stu-id="ce6e4-144">See also</span></span>
* [<span data-ttu-id="ce6e4-145">Buscar, instalar y desinstalar aplicaciones del Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="ce6e4-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

