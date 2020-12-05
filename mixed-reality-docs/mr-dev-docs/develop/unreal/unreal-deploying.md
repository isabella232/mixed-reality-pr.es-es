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
ms.openlocfilehash: e811bc1b82aa40e658f9c855b65446483dd8bef2
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609436"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="f52cb-104">Implementación en el dispositivo en Unreal</span><span class="sxs-lookup"><span data-stu-id="f52cb-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="f52cb-105">Hay dos maneras de implementar una aplicación no real en HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="f52cb-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="f52cb-106">Directamente desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="f52cb-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="f52cb-107">Como un paquete cargado a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f52cb-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="f52cb-108">Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](../platform-capabilities-and-apis/using-the-windows-device-portal.md) para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f52cb-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="f52cb-109">Implementación en el dispositivo desde el editor desareal</span><span class="sxs-lookup"><span data-stu-id="f52cb-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="f52cb-110">Seleccione la flecha desplegable situada junto al botón **iniciar** .</span><span class="sxs-lookup"><span data-stu-id="f52cb-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="f52cb-111">Inicialmente, la opción de dispositivo HoloLens estará atenuada.</span><span class="sxs-lookup"><span data-stu-id="f52cb-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="f52cb-113">Abra el **Device Manager** y tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f52cb-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="f52cb-114">Expanda la sección **Agregar un dispositivo** que no está en la lista.</span><span class="sxs-lookup"><span data-stu-id="f52cb-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="f52cb-115">Seleccione **HoloLens** como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="f52cb-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="f52cb-116">Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f52cb-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="f52cb-117">Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB).</span><span class="sxs-lookup"><span data-stu-id="f52cb-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="f52cb-118">Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f52cb-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="f52cb-119">Presione **Agregar** y cierre el administrador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f52cb-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="f52cb-120">Si hay un error, como una dirección o credenciales de usuario incorrectas, se imprimirá un mensaje en el registro de salida.</span><span class="sxs-lookup"><span data-stu-id="f52cb-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="f52cb-122">Seleccione de nuevo la flecha desplegable situada junto al botón **iniciar** . esta vez debería ver el dispositivo HoloLens que acaba de agregar.</span><span class="sxs-lookup"><span data-stu-id="f52cb-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="f52cb-123">Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f52cb-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="f52cb-124">La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="f52cb-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="f52cb-125">No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo).</span><span class="sxs-lookup"><span data-stu-id="f52cb-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="f52cb-126">De lo contrario, se producirá un error de compilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="f52cb-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="f52cb-127">Implementación en el dispositivo a través del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f52cb-127">Deploying to device via device portal</span></span>

<span data-ttu-id="f52cb-128">Puede encontrar instrucciones detalladas sobre cómo empaquetar e implementar una aplicación en la [serie de tutoriales inreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="f52cb-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f52cb-129">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="f52cb-129">Next Development Checkpoint</span></span>

<span data-ttu-id="f52cb-130">Si está siguiendo el viaje de desarrollo no real que hemos diseñado, se encuentra en medio de la fase de implementación.</span><span class="sxs-lookup"><span data-stu-id="f52cb-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="f52cb-131">Desde aquí, puede seguir agregando Advanced Services:</span><span class="sxs-lookup"><span data-stu-id="f52cb-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f52cb-132">Servicios avanzados</span><span class="sxs-lookup"><span data-stu-id="f52cb-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="f52cb-133">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="f52cb-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
