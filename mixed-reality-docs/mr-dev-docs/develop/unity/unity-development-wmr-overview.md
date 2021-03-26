---
title: Desarrollo de Unity para VR
description: Introducción a la compilación de aplicaciones de realidad mixta en Unity para VR y cascos envolventes de Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidad mixta, mixed reality, desarrollo, introducción, nuevo proyecto, portabilidad, funcionalidad, cámara, simulación, emulación, documentación, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, qué es la realidad virtual, qué es la realidad aumentada, MRTK, kit de herramientas de realidad mixta, entrada de voz, cámara localizable, emulador, Azure, tutoriales
ms.openlocfilehash: e80c5411c7d180e0d78e031599455235dabaceb7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237146"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="00a6d-104">Desarrollo de Unity para VR y Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="00a6d-104">Unity development for VR and Windows Mixed Reality</span></span>

![Logotipo del banner de Unity](../images/unity_logo_banner.png)

<span data-ttu-id="00a6d-106">Si no está familiarizado con Unity, le recomendamos que explore los [tutoriales](https://unity3d.com/learn/tutorials) de nivel principiante en la plataforma de aprendizaje de Unity antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="00a6d-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="00a6d-107">También puede resultarle útil visitar los [foros de Mixed Reality de Unity](https://forum.unity3d.com/forums/hololens.102/) a fin de interactuar con la comunidad en línea que compila aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="00a6d-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="00a6d-108">Nunca se sabe qué recursos o soluciones interesantes pueden encontrarse allí.</span><span class="sxs-lookup"><span data-stu-id="00a6d-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="00a6d-109">Cuando esté listo para empezar a usar MRTK, diríjase a los puntos de control de desarrollo siguientes.</span><span class="sxs-lookup"><span data-stu-id="00a6d-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00a6d-110">Eche un vistazo a nuestras **[guías de migración](../porting-apps/porting-overview.md)** si tiene un proyecto de Unity existente que quiere llevar a un casco envolvente de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="00a6d-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="00a6d-111">Puntos de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="00a6d-111">Development checkpoints</span></span>

<span data-ttu-id="00a6d-112">Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="00a6d-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="00a6d-113">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="00a6d-113">1. Getting started</span></span>

<span data-ttu-id="00a6d-114">Hay un pequeño conjunto de opciones de configuración de Unity que debe cambiar manualmente para el desarrollo de Windows Mixed Reality y VR.</span><span class="sxs-lookup"><span data-stu-id="00a6d-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="00a6d-115">Se dividen en dos categorías: por proyecto y por escena.</span><span class="sxs-lookup"><span data-stu-id="00a6d-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="00a6d-116">Al final de esta sección, tendrá las herramientas y la configuración del proyecto para empezar a crear sus propias aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="00a6d-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="00a6d-117">Punto de control</span><span class="sxs-lookup"><span data-stu-id="00a6d-117">Checkpoint</span></span>  |  <span data-ttu-id="00a6d-118">Resultado</span><span class="sxs-lookup"><span data-stu-id="00a6d-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="00a6d-119">Instale las actualizaciones más recientes.</span><span class="sxs-lookup"><span data-stu-id="00a6d-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="00a6d-120">Descargue e instale el paquete de Unity más reciente y configure el proyecto para la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="00a6d-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="00a6d-121">Configuración del proyecto para WMR</span><span class="sxs-lookup"><span data-stu-id="00a6d-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="00a6d-122">Obtenga información sobre cómo compilar aplicaciones que representen contenido digital en dispositivos de pantalla holográfica y VR.</span><span class="sxs-lookup"><span data-stu-id="00a6d-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="00a6d-123">2. Bloques de creación principales</span><span class="sxs-lookup"><span data-stu-id="00a6d-123">2. Core building blocks</span></span>

<span data-ttu-id="00a6d-124">Después de iniciar un nuevo proyecto envolvente, necesitará algunos bloques de creación básicos para desarrollar aplicaciones envolventes.</span><span class="sxs-lookup"><span data-stu-id="00a6d-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="00a6d-125">Todos los bloques de creación básicos para las aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity.</span><span class="sxs-lookup"><span data-stu-id="00a6d-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="00a6d-126">Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio.</span><span class="sxs-lookup"><span data-stu-id="00a6d-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="00a6d-127">Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en un proyecto de VR.</span><span class="sxs-lookup"><span data-stu-id="00a6d-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="00a6d-128">3. Características avanzadas</span><span class="sxs-lookup"><span data-stu-id="00a6d-128">3. Advanced features</span></span>

<span data-ttu-id="00a6d-129">Hay otras características clave que desempeñan un rol en las aplicaciones envolventes disponibles a través de las API de Unity sin que se requiera ningún paquete o instalación adicional.</span><span class="sxs-lookup"><span data-stu-id="00a6d-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="00a6d-130">Después de profundizar en las funcionalidades más avanzadas que ofrece Unity, podrá crear aplicaciones de VR más completas y complejas.</span><span class="sxs-lookup"><span data-stu-id="00a6d-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="00a6d-131">Característica</span><span class="sxs-lookup"><span data-stu-id="00a6d-131">Feature</span></span>  |  <span data-ttu-id="00a6d-132">Funcionalidades</span><span class="sxs-lookup"><span data-stu-id="00a6d-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="00a6d-133">Pérdida de seguimiento</span><span class="sxs-lookup"><span data-stu-id="00a6d-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="00a6d-134">Permite controlar los escenarios en los que el dispositivo no se encuentra en el espacio del mundo de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="00a6d-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="00a6d-135">Entrada de teclado</span><span class="sxs-lookup"><span data-stu-id="00a6d-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="00a6d-136">Permite obtener información sobre los teclados del mundo real y de la realidad mixta en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="00a6d-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="00a6d-137">4. Implementación en un dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="00a6d-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="00a6d-138">Una vez que tengas el proyecto holográfico de Unity listo para las pruebas, el paso siguiente consiste en exportar y compilar una solución de Visual Studio de Unity.</span><span class="sxs-lookup"><span data-stu-id="00a6d-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="00a6d-139">Teniendo en cuenta esa solución de VS, puede ejecutar su aplicación en dispositivos reales o simulados.</span><span class="sxs-lookup"><span data-stu-id="00a6d-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="00a6d-140">Al final de esta sección, podrá implementar la aplicación en un dispositivo o emulador que se adapte a sus necesidades de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="00a6d-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="00a6d-141">Casco envolvente de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="00a6d-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="00a6d-142">Simulador del casco envolvente de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="00a6d-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="00a6d-143">¿Qué sigue?</span><span class="sxs-lookup"><span data-stu-id="00a6d-143">What's next?</span></span>

<span data-ttu-id="00a6d-144">Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK.</span><span class="sxs-lookup"><span data-stu-id="00a6d-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="00a6d-145">En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado.</span><span class="sxs-lookup"><span data-stu-id="00a6d-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="00a6d-146">Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.</span><span class="sxs-lookup"><span data-stu-id="00a6d-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="00a6d-147">Migración</span><span class="sxs-lookup"><span data-stu-id="00a6d-147">Porting</span></span>

<span data-ttu-id="00a6d-148">Si tiene aplicaciones que quiere migrar, consulte los artículos que se enumeran a continuación:</span><span class="sxs-lookup"><span data-stu-id="00a6d-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="00a6d-149">Portabilidad de aplicaciones de VR a Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="00a6d-149">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="00a6d-150">Actualización de aplicaciones de SteamVR para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="00a6d-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="00a6d-151">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="00a6d-151">Additional resources</span></span>

<span data-ttu-id="00a6d-152">Antes de que se sumerja en el mundo de la realidad mixta por su cuenta, le recomendamos que eche un vistazo a la documentación adicional que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="00a6d-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="00a6d-153">Guía para entusiastas de la realidad virtual</span><span class="sxs-lookup"><span data-stu-id="00a6d-153">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="00a6d-154">Almacén de recursos de Unity</span><span class="sxs-lookup"><span data-stu-id="00a6d-154">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="00a6d-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="00a6d-155">See also</span></span> 

* [<span data-ttu-id="00a6d-156">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="00a6d-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="00a6d-157">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="00a6d-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="00a6d-158">Exportación y creación de una solución de Visual Studio para Unity</span><span class="sxs-lookup"><span data-stu-id="00a6d-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="00a6d-159">Procedimientos recomendados para trabajar con Unity y Visual Studio</span><span class="sxs-lookup"><span data-stu-id="00a6d-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)