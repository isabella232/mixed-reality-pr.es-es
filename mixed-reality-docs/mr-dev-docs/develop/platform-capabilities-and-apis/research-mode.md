---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens, HoloLens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237136"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="de088-104">Modo de investigación de HoloLens</span><span class="sxs-lookup"><span data-stu-id="de088-104">HoloLens Research Mode</span></span>

<span data-ttu-id="de088-105">El modo de investigación se presentó en los dispositivos de HoloLens (primera generación) para dar acceso a los sensores clave, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.</span><span class="sxs-lookup"><span data-stu-id="de088-105">Research Mode was introduced on HoloLens (1st Gen) devices to give access to key sensors, specifically for research applications that aren't intended for deployment.</span></span>  <span data-ttu-id="de088-106">El modo de investigación de HoloLens 2 mantiene las capacidades de HoloLens 1, pero agrega acceso a los siguientes flujos:</span><span class="sxs-lookup"><span data-stu-id="de088-106">Research Mode for HoloLens 2 keeps the capabilities of HoloLens 1 but adds access to the following streams:</span></span>

* <span data-ttu-id="de088-107">**Cámaras de seguimiento de entornos claros visibles** : cámaras de escala de grises usadas por el sistema para el seguimiento de los cabezales y el edificio de mapas.</span><span class="sxs-lookup"><span data-stu-id="de088-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="de088-108">**Cámara de profundidad** : funciona en dos modos:</span><span class="sxs-lookup"><span data-stu-id="de088-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="de088-109">Detección de profundidad de AHAT, alta frecuencia (45 FPS) utilizada para el seguimiento manual.</span><span class="sxs-lookup"><span data-stu-id="de088-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="de088-110">De forma diferente al modo de inicio de la primera versión, AHAT proporciona una pseudo profundidad con ajuste de fase superior a 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="de088-110">Differently from the first version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="de088-111">Detección de profundidad larga de baja frecuencia (1-5 FPS) usada por la [asignación espacial](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="de088-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="de088-112">**Dos versiones de la secuencia ir-reflectividad** : usadas por HoloLens para calcular la profundidad.</span><span class="sxs-lookup"><span data-stu-id="de088-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="de088-113">Estas imágenes se iluminan por infrarrojos y no se ven afectadas por la luz visible de ambiente.</span><span class="sxs-lookup"><span data-stu-id="de088-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="de088-114">Si usa HoloLens 2, también tiene acceso a las entradas adicionales siguientes:</span><span class="sxs-lookup"><span data-stu-id="de088-114">If you're using a HoloLens 2, you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="de088-115">**Acelerómetro** : lo usa el sistema para determinar la aceleración lineal a lo largo de los ejes X, y y Z y la gravedad.</span><span class="sxs-lookup"><span data-stu-id="de088-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y, and Z axes and gravity.</span></span>
* <span data-ttu-id="de088-116">**Gyro** : el sistema lo usa para determinar los giros.</span><span class="sxs-lookup"><span data-stu-id="de088-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="de088-117">**Magnetómetro** : lo usa el sistema para calcular la orientación absoluta.</span><span class="sxs-lookup"><span data-stu-id="de088-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de088-118">El modo de investigación está actualmente en versión preliminar pública.</span><span class="sxs-lookup"><span data-stu-id="de088-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="de088-119">![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="de088-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="de088-120">*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*</span><span class="sxs-lookup"><span data-stu-id="de088-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="de088-121">Uso</span><span class="sxs-lookup"><span data-stu-id="de088-121">Usage</span></span>

<span data-ttu-id="de088-122">El modo de investigación está diseñado para investigadores académicos e industriales que exploran ideas nuevas en los campos de Computer Vision y robótica.</span><span class="sxs-lookup"><span data-stu-id="de088-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="de088-123">No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través del Microsoft Store u otros canales de distribución.</span><span class="sxs-lookup"><span data-stu-id="de088-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="de088-124">Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se admitirán en futuras actualizaciones de hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="de088-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="de088-125">Sin embargo, no deje que le dejen de usarlo para desarrollar y probar ideas nuevas.</span><span class="sxs-lookup"><span data-stu-id="de088-125">However, don't let that stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="de088-126">Seguridad y rendimiento</span><span class="sxs-lookup"><span data-stu-id="de088-126">Security and performance</span></span>

<span data-ttu-id="de088-127">Al habilitar el modo de investigación se usa más energía de la batería que el uso de HoloLens 2 en condiciones normales, aunque no se esté ejecutando la aplicación que usa las características del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="de088-127">Enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions, even if the application using the Research Mode features isn't running.</span></span>  <span data-ttu-id="de088-128">Habilitar este modo también puede reducir la seguridad general del dispositivo, ya que las aplicaciones pueden hacer uso indebido de los datos del sensor.</span><span class="sxs-lookup"><span data-stu-id="de088-128">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="de088-129">Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes sobre seguridad de HoloLens](/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="de088-129">You can find more information on device security in the [HoloLens security FAQ](/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="de088-130">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="de088-130">Device support</span></span>
<table><span data-ttu-id="de088-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="de088-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="de088-132"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="de088-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="de088-133"><a href="/hololens/hololens1-hardware"><strong>Primera generación de HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="de088-133"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="de088-134"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="de088-134"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="de088-135">Cámaras de seguimiento de cabezales</span><span class="sxs-lookup"><span data-stu-id="de088-135">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="de088-136">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-136">✔️</span></span></td>
        <td><span data-ttu-id="de088-137">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-137">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="de088-138">Profundidad & cámara de INFRARROJOs</span><span class="sxs-lookup"><span data-stu-id="de088-138">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="de088-139">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-139">✔️</span></span></td>
        <td><span data-ttu-id="de088-140">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-140">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="de088-141">Acelerómetro</span><span class="sxs-lookup"><span data-stu-id="de088-141">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="de088-142">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="de088-143">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="de088-143">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="de088-144">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="de088-145">Magnetómetro</span><span class="sxs-lookup"><span data-stu-id="de088-145">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="de088-146">✔️</span><span class="sxs-lookup"><span data-stu-id="de088-146">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a><span data-ttu-id="de088-147">Habilitación del modo de investigación (HoloLens First gen y HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="de088-147">Enabling Research Mode (HoloLens first Gen and HoloLens 2)</span></span>

<span data-ttu-id="de088-148">El modo de investigación es una extensión del modo de programador.</span><span class="sxs-lookup"><span data-stu-id="de088-148">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="de088-149">Antes de comenzar, las características del desarrollador del dispositivo deben estar habilitadas para tener acceso a la configuración del modo de investigación:</span><span class="sxs-lookup"><span data-stu-id="de088-149">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="de088-150">Abra el **menú inicio > configuración** y seleccione **actualizaciones**.</span><span class="sxs-lookup"><span data-stu-id="de088-150">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="de088-151">Seleccione **para desarrolladores** y habilite el **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="de088-151">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="de088-152">Desplázate hacia abajo y habilita **Portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="de088-152">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="de088-153">Una vez habilitadas las características de desarrollador, [Conéctese al portal de dispositivos](/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación:</span><span class="sxs-lookup"><span data-stu-id="de088-153">After the developer features  are enabled, [connect to the device portal](/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="de088-154">Vaya al **modo System > Research** en el **portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="de088-154">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="de088-155">Seleccione **permitir el acceso a la secuencia del sensor**.</span><span class="sxs-lookup"><span data-stu-id="de088-155">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="de088-156">Reinicie el dispositivo desde el elemento de menú de **energía** en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="de088-156">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="de088-157">Una vez que haya reiniciado el dispositivo, las aplicaciones que se cargan a través del **portal de dispositivos** pueden acceder a los flujos del modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="de088-157">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="de088-158">![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="de088-158">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="de088-159">*Ventana del modo de investigación en el portal de dispositivos de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="de088-159">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de088-160">El modo de investigación de HoloLens 2 está disponible a partir de la compilación 19041,1364.</span><span class="sxs-lookup"><span data-stu-id="de088-160">Research Mode for HoloLens 2 is available beginning with build 19041.1364 .</span></span> <span data-ttu-id="de088-161">Si necesita tener acceso en una compilación anterior, Regístrese en el programa de [versión preliminar de Insider](/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="de088-161">If you need access in an earlier build, sign up for our [Insider Preview](/hololens/hololens-insider) program.</span></span> <span data-ttu-id="de088-162">Puede encontrar más detalles en el [repositorio de github del modo de investigación](https://github.com/microsoft/HoloLens2ForCV).</span><span class="sxs-lookup"><span data-stu-id="de088-162">You can find more details in the [Research Mode GitHub repository](https://github.com/microsoft/HoloLens2ForCV).</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="de088-163">Uso de datos de sensor en las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="de088-163">Using sensor data in your apps</span></span>

<span data-ttu-id="de088-164">Las aplicaciones pueden tener acceso a los datos del flujo del sensor de la misma manera que [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) accede a las secuencias de la cámara de vídeo y de fotos.</span><span class="sxs-lookup"><span data-stu-id="de088-164">Applications can access the sensor stream data in the same way that [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) accesses photo and video camera streams.</span></span> 

<span data-ttu-id="de088-165">Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación.</span><span class="sxs-lookup"><span data-stu-id="de088-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="de088-166">En concreto, la aplicación sabe exactamente dónde se encuentra HoloLens en el espacio 6DoF en cada tiempo de captura de fotogramas del sensor.</span><span class="sxs-lookup"><span data-stu-id="de088-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="de088-167">Tenemos aplicaciones de ejemplo en las que se muestra el acceso a secuencias en modo de referencia, con los [intrínsecos y extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)y las secuencias de registro:</span><span class="sxs-lookup"><span data-stu-id="de088-167">We have sample applications showing Research Mode stream access, using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams:</span></span>
* [<span data-ttu-id="de088-168">HoloLens (primera generación)</span><span class="sxs-lookup"><span data-stu-id="de088-168">HoloLens (first gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="de088-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="de088-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="de088-170">Soporte técnico</span><span class="sxs-lookup"><span data-stu-id="de088-170">Support</span></span>

<span data-ttu-id="de088-171">Para HoloLens (primera generación), use el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.</span><span class="sxs-lookup"><span data-stu-id="de088-171">For HoloLens (first gen), use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="de088-172">Para HoloLens 2, use el [seguimiento de problemas](https://github.com/microsoft/HoloLens2ForCV/issues) en el repositorio de HoloLens2ForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.</span><span class="sxs-lookup"><span data-stu-id="de088-172">For HoloLens 2, use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="de088-173">Consulte también</span><span class="sxs-lookup"><span data-stu-id="de088-173">See also</span></span>

* [<span data-ttu-id="de088-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="de088-174">Microsoft Media Foundation</span></span>](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [<span data-ttu-id="de088-175">Repositorio de GitHub de HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="de088-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="de088-176">Repositorio de GitHub de HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="de088-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="de088-177">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="de088-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)