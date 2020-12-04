---
title: Implementación en el dispositivo en Unreal
description: Guía para la implementación en el dispositivo de un equipo inreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, PC, documentación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: ef33e037d6ab6a69059c1452b71a428fe51836b9
ms.sourcegitcommit: d56e7dd6c917ddc4ead0792ebff21891921174b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564025"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="f618a-104">Implementación en el dispositivo en Unreal</span><span class="sxs-lookup"><span data-stu-id="f618a-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f618a-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="f618a-105">Overview</span></span>
<span data-ttu-id="f618a-106">Hay dos maneras de implementar una aplicación no real en HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="f618a-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="f618a-107">Directamente desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="f618a-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="f618a-108">Como un paquete cargado a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f618a-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="f618a-109">Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f618a-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="f618a-110">Implementación en el dispositivo desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="f618a-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="f618a-111">Haga clic en la flecha desplegable situada junto al botón **iniciar** .</span><span class="sxs-lookup"><span data-stu-id="f618a-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="f618a-112">Inicialmente, la opción de dispositivo HoloLens estará atenuada.</span><span class="sxs-lookup"><span data-stu-id="f618a-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="f618a-114">Abra el **Device Manager**.</span><span class="sxs-lookup"><span data-stu-id="f618a-114">Open the **Device Manager**.</span></span> <span data-ttu-id="f618a-115">Tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f618a-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="f618a-116">Expanda la sección **Agregar un dispositivo** que no está en la lista.</span><span class="sxs-lookup"><span data-stu-id="f618a-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="f618a-117">Seleccione **HoloLens** como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="f618a-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="f618a-118">Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f618a-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="f618a-119">Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB).</span><span class="sxs-lookup"><span data-stu-id="f618a-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="f618a-120">Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f618a-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="f618a-121">Presione **Agregar** y cierre el administrador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f618a-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="f618a-122">En el caso de un error (por ejemplo, una dirección incorrecta, un nombre de usuario o una contraseña), se imprimirá un mensaje en el registro de salida.</span><span class="sxs-lookup"><span data-stu-id="f618a-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="f618a-124">Haga clic en la flecha desplegable situada junto al botón **Launch (iniciar** ) de nuevo; esta vez debería ver el dispositivo HoloLens que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="f618a-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="f618a-125">Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f618a-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="f618a-126">La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="f618a-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="f618a-127">No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo).</span><span class="sxs-lookup"><span data-stu-id="f618a-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="f618a-128">De lo contrario, se producirá un error de compilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="f618a-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="f618a-129">Implementación en el dispositivo a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f618a-129">Deploying to device via device portal</span></span>

<span data-ttu-id="f618a-130">Puede encontrar instrucciones detalladas sobre cómo [empaquetar e implementar una aplicación](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) en la última sección del introducción con una serie de tutoriales inreal.</span><span class="sxs-lookup"><span data-stu-id="f618a-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f618a-131">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="f618a-131">Next Development Checkpoint</span></span>

<span data-ttu-id="f618a-132">Si está siguiendo el viaje de punto de control de desarrollo no real que hemos diseñado, se encuentra en medio de la fase de implementación.</span><span class="sxs-lookup"><span data-stu-id="f618a-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="f618a-133">Desde aquí, puede seguir agregando Advanced Services:</span><span class="sxs-lookup"><span data-stu-id="f618a-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f618a-134">Servicios avanzados</span><span class="sxs-lookup"><span data-stu-id="f618a-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="f618a-135">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="f618a-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
