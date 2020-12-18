---
title: Streaming en Unreal
description: Guía de streaming de Unreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, streaming, PC, holographic app remoting, holographic remoting player, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 3638f07753355061f251bb2d6fa47233872d5b90
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855892"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="b6f17-104">Streaming en Unreal</span><span class="sxs-lookup"><span data-stu-id="b6f17-104">Streaming in Unreal</span></span>

<span data-ttu-id="b6f17-105">El streaming de un equipo a HoloLens ofrece dos ventajas principales:</span><span class="sxs-lookup"><span data-stu-id="b6f17-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="b6f17-106">Permite que la aplicación de realidad mixta aproveche la eficacia de cálculo de los equipos.</span><span class="sxs-lookup"><span data-stu-id="b6f17-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="b6f17-107">Ayuda a acelerar el tiempo de iteración de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="b6f17-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="b6f17-108">Para empezar, deberá descargar [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) en su dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b6f17-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="b6f17-109">Holographic Remoting Player permitirá que la aplicación transmita directamente al reproductor de control remoto en HoloLens desde los orígenes siguientes:</span><span class="sxs-lookup"><span data-stu-id="b6f17-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="b6f17-110">Editor Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="b6f17-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="b6f17-111">Ejecutable de Windows empaquetado</span><span class="sxs-lookup"><span data-stu-id="b6f17-111">A packaged Windows executable</span></span> 

<span data-ttu-id="b6f17-112">Durante el streaming, tiene acceso prácticamente a las mismas funcionalidades de HoloLens que cuando se ejecuta una aplicación en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b6f17-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="b6f17-113">Esto incluye [seguimiento de articulación de la mano](unreal-hand-tracking.md) (si utiliza HoloLens 2), [asignación espacial](unreal-spatial-mapping.md) y [anclajes espaciales](unreal-spatial-anchors.md), pero descarta las características de esta [lista](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="b6f17-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="b6f17-114">La calidad de streaming depende en gran medida de la intensidad de la señal de su red WiFi.</span><span class="sxs-lookup"><span data-stu-id="b6f17-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="b6f17-115">Todas las funciones se habilitan automáticamente para la aplicación Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="b6f17-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="b6f17-116">Si encuentra una funcionalidad que requiere permiso del usuario (p. ej., el seguimiento ocular) para funcionar en streaming, pero no cuando se ejecuta en el dispositivo, asegúrese de haber habilitado las funcionalidades adecuadas en la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b6f17-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="b6f17-117">Limitaciones de streaming</span><span class="sxs-lookup"><span data-stu-id="b6f17-117">Streaming limitations</span></span>

<span data-ttu-id="b6f17-118">Las mallas de mano, la cámara de HoloLens y el teclado del sistema no están disponibles a través de streaming.</span><span class="sxs-lookup"><span data-stu-id="b6f17-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="b6f17-119">Tenga en cuenta que la entrada de voz para las aplicaciones transmitidas se puede adquirir a través del micrófono del equipo desde el que se hace streaming.</span><span class="sxs-lookup"><span data-stu-id="b6f17-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="b6f17-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b6f17-120">OpenXR</span></span>

<span data-ttu-id="b6f17-121">Unreal 4.26 en ejecución en OpenXR admite el streaming a las versiones 2.4.0 o posteriores del reproductor de control remoto de holografías.</span><span class="sxs-lookup"><span data-stu-id="b6f17-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="b6f17-122">El streaming de OpenXR en la versión 2.4.0 no tiene compatibilidad con la asignación espacial y los anclajes espaciales.</span><span class="sxs-lookup"><span data-stu-id="b6f17-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="b6f17-123">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="b6f17-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b6f17-124"><strong>Origen</strong></span><span class="sxs-lookup"><span data-stu-id="b6f17-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="b6f17-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>Primera generación de HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b6f17-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="b6f17-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="b6f17-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="b6f17-127"><strong>Cascos envolventes</strong></span><span class="sxs-lookup"><span data-stu-id="b6f17-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b6f17-128">Editor de Unreal</span><span class="sxs-lookup"><span data-stu-id="b6f17-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="b6f17-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b6f17-129">✔️</span></span></td>
        <td><span data-ttu-id="b6f17-130">✔️</span><span class="sxs-lookup"><span data-stu-id="b6f17-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="b6f17-131">Paquetes de Windows</span><span class="sxs-lookup"><span data-stu-id="b6f17-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b6f17-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b6f17-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="b6f17-133">Streaming desde el editor de Unreal</span><span class="sxs-lookup"><span data-stu-id="b6f17-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="b6f17-134">Como desarrollador, descubrirá que el streaming desde el editor de Unreal a su dispositivo HoloLens proporciona ventajas importantes al realizar pruebas; por ejemplo, ya no tiene que esperar a que la aplicación se compile e implemente antes de probar las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b6f17-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="b6f17-135">Puede encontrar instrucciones detalladas sobre el [streaming desde el editor de Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) en nuestra serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="b6f17-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="b6f17-136">Streaming desde un ejecutable de Windows empaquetado</span><span class="sxs-lookup"><span data-stu-id="b6f17-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="b6f17-137">En Unreal 4.25.1, puede transmitir la aplicación a un dispositivo HoloLens 2 desde un ejecutable de Windows empaquetado:</span><span class="sxs-lookup"><span data-stu-id="b6f17-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="b6f17-138">Vaya a **File > Package Project > Windows** (Archivo > Proyecto de paquete > Windows) en el menú del editor.</span><span class="sxs-lookup"><span data-stu-id="b6f17-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="b6f17-139">Elija una ubicación donde guardar el paquete y seleccione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="b6f17-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="b6f17-140">Una vez que el paquete termine de compilarse, abra **Holographic Remoting Player** en HoloLens 2 y tome nota de la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="b6f17-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="b6f17-141">Deje **Holographic Remoting Player** abierto y en el símbolo del sistema:</span><span class="sxs-lookup"><span data-stu-id="b6f17-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="b6f17-142">Invoque cd en el directorio local donde guardó el paquete.</span><span class="sxs-lookup"><span data-stu-id="b6f17-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="b6f17-143">Escriba el comando siguiente: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="b6f17-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="b6f17-144">El nombre de la aplicación en la configuración del proyecto debe usarse automáticamente para crear el paquete de Windows.</span><span class="sxs-lookup"><span data-stu-id="b6f17-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="b6f17-145">Si por alguna razón son diferentes, utilice el nombre del ejecutable de Windows en el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="b6f17-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="b6f17-146">Presione Entrar y observe que la aplicación inicia el streaming.</span><span class="sxs-lookup"><span data-stu-id="b6f17-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="b6f17-147">Opciones de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="b6f17-147">Command line options</span></span>

<span data-ttu-id="b6f17-148">En la tabla siguiente, se pueden encontrar opciones adicionales de la línea de comandos para hacer streaming desde cada plataforma de Unreal Engine 4.26 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="b6f17-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="b6f17-149">Consulta también</span><span class="sxs-lookup"><span data-stu-id="b6f17-149">See also</span></span>

* [<span data-ttu-id="b6f17-150">Historial de versiones de Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="b6f17-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="b6f17-151">Escritura de una aplicación de reproductor de control remoto de holografías personalizada</span><span class="sxs-lookup"><span data-stu-id="b6f17-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="b6f17-152">Establecimiento de una conexión segura con Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="b6f17-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
