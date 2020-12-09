---
title: Distribución de las aplicaciones
description: Información general de las diferentes opciones de distribución para distintas plataformas y almacenes de publicación compatibles.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realidad mixta, auriculares envolventes, aplicación, UWP, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, Wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: 5c7a1d6e00610a4046bd71b07ca5184399c9e335
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925778"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="df3cd-104">Distribución de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="df3cd-104">Distributing your apps</span></span>

![Lancher de aplicación 3D de pájaros de punto flotante en WMR Home](images/distribute-hero-image.png)

<span data-ttu-id="df3cd-106">La obtención de las aplicaciones en manos de los usuarios o en el mundo es la más importante y a veces PAINSTAKING, parte de cualquier esfuerzo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="df3cd-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="df3cd-107">Hemos simplificado el proceso en un conjunto de recursos que se enumeran a continuación, que dependen del escenario de distribución e implementación que mejor se adapte a usted o a su equipo.</span><span class="sxs-lookup"><span data-stu-id="df3cd-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="df3cd-108">Opciones de distribución</span><span class="sxs-lookup"><span data-stu-id="df3cd-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="df3cd-109">Si va a compartir la aplicación con otra entidad, debe compilar y proporcionar el archivo appx.</span><span class="sxs-lookup"><span data-stu-id="df3cd-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="df3cd-110">Si usa el instalador de aplicaciones, también necesitará compartir el certificado con el usuario.</span><span class="sxs-lookup"><span data-stu-id="df3cd-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="df3cd-111">Si está compartiendo con una organización, necesita una cuenta profesional o educativa y acceso a la infraestructura de [MDM (administración de dispositivos móviles)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) de las organizaciones.</span><span class="sxs-lookup"><span data-stu-id="df3cd-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="df3cd-112">Si es la entidad de uso compartido, debe ser administrador en el inquilino y usar el centro de [Administración de Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) para que la aplicación esté disponible.</span><span class="sxs-lookup"><span data-stu-id="df3cd-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="df3cd-113">Otra opción es compartir el archivo appx y las dependencias de la aplicación con el usuario final.</span><span class="sxs-lookup"><span data-stu-id="df3cd-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="df3cd-114">Si es el usuario final, la aplicación se descargará automáticamente o estará disponible para su descarga una vez que se inscriba en el inquilino de la organización de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="df3cd-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="df3cd-115"><strong>Escenario</strong></span><span class="sxs-lookup"><span data-stu-id="df3cd-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="df3cd-116"><strong>Instalación de dispositivo local</strong></span><span class="sxs-lookup"><span data-stu-id="df3cd-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="df3cd-117"><strong>Compartir con cualquier persona</strong></span><span class="sxs-lookup"><span data-stu-id="df3cd-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="df3cd-118"><strong>Compartir con una organización</strong></span><span class="sxs-lookup"><span data-stu-id="df3cd-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Instalador de aplicaciones</strong></a> (a través de <a href="https://docs.microsoft.com/hololens/hololens-insider">compilaciones de Windows Insider</a>)</span><span class="sxs-lookup"><span data-stu-id="df3cd-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></a> (through <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider builds</a>)</span></span></td>
    <td><span data-ttu-id="df3cd-120">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-120">✔️</span></span></td>
    <td><span data-ttu-id="df3cd-121">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Portal de empresa MDM</strong></a></span><span class="sxs-lookup"><span data-stu-id="df3cd-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="df3cd-123">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM: instalación de la aplicación requerida</strong></a></span><span class="sxs-lookup"><span data-stu-id="df3cd-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="df3cd-125">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="df3cd-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="df3cd-127">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-127">✔️</span></span></td>
    <td><span data-ttu-id="df3cd-128">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store para Empresas</strong></a></span><span class="sxs-lookup"><span data-stu-id="df3cd-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="df3cd-130">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Paquete de aprovisionamiento</strong></a></span><span class="sxs-lookup"><span data-stu-id="df3cd-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="df3cd-132">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-132">✔️</span></span></td>
    <td><span data-ttu-id="df3cd-133">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-133">✔️</span></span></td>
    <td><span data-ttu-id="df3cd-134">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="df3cd-135"><a href="#additional-scenarios"><strong>Implementación personalizada de Win32</strong></a> (no está disponible para dispositivos HoloLens; consulte a continuación).</span><span class="sxs-lookup"><span data-stu-id="df3cd-135"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="df3cd-136">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-136">✔️</span></span></td>
    <td><span data-ttu-id="df3cd-137">✔️</span><span class="sxs-lookup"><span data-stu-id="df3cd-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="df3cd-138">El instalador de la aplicación no está disponible actualmente para dispositivos administrados o de HoloLens (primera generación).</span><span class="sxs-lookup"><span data-stu-id="df3cd-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="df3cd-139">Otros escenarios</span><span class="sxs-lookup"><span data-stu-id="df3cd-139">Additional scenarios</span></span>

* <span data-ttu-id="df3cd-140">En el caso de la implementación de aplicaciones Win32, incluida la secuencia de vapor y la de juegos, puede generar un Win32. Archivo EXE que usa el destino de compilación independiente de PC de Unity y envíe las aplicaciones de la forma habitual a la plataforma elegida.</span><span class="sxs-lookup"><span data-stu-id="df3cd-140">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="df3cd-141">Si tiene que instalar una aplicación de HoloLens 2 mientras está sin conexión, consulte las instrucciones [seguras de hololens 2 sin conexión](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) o instale la aplicación a través de un paquete de aprovisionamiento sin habilitar el modo de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="df3cd-141">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="df3cd-142">También puede implementar compilaciones en el dispositivo y compartirlas con otros desarrolladores que tengan el modo de desarrollador habilitado mediante la [implementación y depuración con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o [la instalación de un paquete de aplicación con el portal de dispositivos](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="df3cd-142">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="df3cd-143">Consulte también</span><span class="sxs-lookup"><span data-stu-id="df3cd-143">See also</span></span>
* [<span data-ttu-id="df3cd-144">Buscar, instalar y desinstalar aplicaciones del Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="df3cd-144">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
