---
title: Preguntas más frecuentes sobre seguimiento
description: Seguimiento de la solución de problemas de Windows Mixed Reality que va más allá de nuestra documentación de soporte técnico de consumidor estándar.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, seguimiento
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725836"
---
# <a name="tracking-faqs"></a><span data-ttu-id="f7502-104">Preguntas más frecuentes sobre seguimiento</span><span class="sxs-lookup"><span data-stu-id="f7502-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="f7502-105">El micrófono ha dejado de realizar el seguimiento</span><span class="sxs-lookup"><span data-stu-id="f7502-105">My headset has stopped tracking</span></span>

<span data-ttu-id="f7502-106">Asegúrese de que las luces están encendidas y de que no hay nada que obstruya las cámaras de seguimiento interior de la parte delantera del casco.</span><span class="sxs-lookup"><span data-stu-id="f7502-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="f7502-107">Si se pierde el seguimiento, puede tardar unos segundos en reanudarse.</span><span class="sxs-lookup"><span data-stu-id="f7502-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="f7502-108">Reiniciar el portal de Windows Mixed Reality el seguimiento no se reinicia.</span><span class="sxs-lookup"><span data-stu-id="f7502-108">Restart the Windows Mixed Reality Portal is tracking doesn't restart.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="f7502-109">Puedo buscar, pero no puedo traducir (Estoy atascado en 3DOF)</span><span class="sxs-lookup"><span data-stu-id="f7502-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="f7502-110">Esto significa que el sistema de seguimiento no puede generar una representación o que la aplicación se ha detenido con los nuevos datos de pose que se van a representar.</span><span class="sxs-lookup"><span data-stu-id="f7502-110">This means that the tracking system can't generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="f7502-111">Para solucionar el problema:</span><span class="sxs-lookup"><span data-stu-id="f7502-111">To fix the issue:</span></span>

* <span data-ttu-id="f7502-112">Asegúrese de que el salón tenga suficiente luz.</span><span class="sxs-lookup"><span data-stu-id="f7502-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="f7502-113">Asegúrese de que el salón tenga suficientes detalles para realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="f7502-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="f7502-114">Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7502-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="f7502-115">Si el mensaje persiste, póngase en contacto [con el servicio de soporte al cliente](https://support.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="f7502-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-frozen"></a><span data-ttu-id="f7502-116">La vista del HMD está inmovilizada</span><span class="sxs-lookup"><span data-stu-id="f7502-116">The view in the HMD is frozen</span></span>

<span data-ttu-id="f7502-117">Normalmente, esto significa que se ha producido un error en la aplicación o en un componente de nivel de sistema.</span><span class="sxs-lookup"><span data-stu-id="f7502-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="f7502-118">Intente:</span><span class="sxs-lookup"><span data-stu-id="f7502-118">Try to:</span></span>

1. <span data-ttu-id="f7502-119">Presione el botón "Inicio" para salir de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f7502-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="f7502-120">Desconecte el dispositivo, cierre PRM y vuelva a conectar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7502-120">Unplug the device, close MRP, and plug the device back in.</span></span>
3. <span data-ttu-id="f7502-121">Reinicia el equipo.</span><span class="sxs-lookup"><span data-stu-id="f7502-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="f7502-122">El mundo se inmovilizó brevemente y se inclina o voltea hacia abajo antes de volver a la normalidad</span><span class="sxs-lookup"><span data-stu-id="f7502-122">The world briefly froze and tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="f7502-123">Esto puede deberse a que una aplicación o un componente de nivel de sistema ha provocado un error irrecuperable o una falta temporal de memoria o recursos de CPU.</span><span class="sxs-lookup"><span data-stu-id="f7502-123">This could be caused by an application or system level component hitting a fatal error or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="f7502-124">Para comprobar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f7502-124">To check:</span></span>

1. <span data-ttu-id="f7502-125">Abra el administrador de tareas y asegúrese de que al menos el 20% de la CPU sea gratuito, 400 MB de memoria disponible y la e/s de disco debe ser inferior al 80%.</span><span class="sxs-lookup"><span data-stu-id="f7502-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400 MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="f7502-126">Vaya a **Visor de eventos > registros de Windows > aplicación** para buscar errores en torno a la inmovilización.</span><span class="sxs-lookup"><span data-stu-id="f7502-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="f7502-127">Busque cualquier elemento que haga referencia a los sensores de HoloLens, la realidad mixta o la aplicación que se estaba ejecutando en ese momento.</span><span class="sxs-lookup"><span data-stu-id="f7502-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="f7502-128">Esos registros podrían explicar qué causó el error.</span><span class="sxs-lookup"><span data-stu-id="f7502-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="f7502-129">Reinicie el equipo si el problema persiste.</span><span class="sxs-lookup"><span data-stu-id="f7502-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="f7502-130">El mundo se invierte momentáneamente hacia abajo y se devolvió a la normalidad</span><span class="sxs-lookup"><span data-stu-id="f7502-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="f7502-131">Esto se debe normalmente a errores en la obtención de datos de sensor desde los auriculares para informar sobre los algoritmos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="f7502-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="f7502-132">Si esto sucede con frecuencia:</span><span class="sxs-lookup"><span data-stu-id="f7502-132">If this happens frequently:</span></span>

1. <span data-ttu-id="f7502-133">Conecte los auriculares a otro puerto USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="f7502-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="f7502-134">Conecte los auriculares directamente al equipo en lugar de a un concentrador USB 3,0.</span><span class="sxs-lookup"><span data-stu-id="f7502-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="f7502-135">Si el problema persiste, póngase en contacto [con el servicio de soporte al cliente](https://support.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="f7502-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="f7502-136">El mundo está inclinado, pero puedo navegar y desplazarse por Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f7502-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="f7502-137">Si los errores de datos del sensor se registran en los datos del entorno del equipo, puede hacer que Windows Mixed Reality aparezca inclinado, a veces permanentemente.</span><span class="sxs-lookup"><span data-stu-id="f7502-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="f7502-138">Para solucionar este error:</span><span class="sxs-lookup"><span data-stu-id="f7502-138">To fix this:</span></span>

1. <span data-ttu-id="f7502-139">Desenchufe los auriculares, cierre Windows Mixed Reality y vuelva a conectar el casco.</span><span class="sxs-lookup"><span data-stu-id="f7502-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="f7502-140">Reinicia el equipo.</span><span class="sxs-lookup"><span data-stu-id="f7502-140">Restart the PC.</span></span>
3. <span data-ttu-id="f7502-141">Borre los datos del entorno.</span><span class="sxs-lookup"><span data-stu-id="f7502-141">Clear your environment data.</span></span>