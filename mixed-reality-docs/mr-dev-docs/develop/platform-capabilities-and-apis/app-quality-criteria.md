---
title: Criterios de calidad de aplicaciones
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: Criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: c18f4e8470f7f183fdf250472fd3a977f925dfbf
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677994"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="30745-104">Criterios de calidad de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="30745-104">App quality criteria</span></span>

<span data-ttu-id="30745-105">En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="30745-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="30745-106">Para cada factor se proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="30745-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="30745-107">Información general: breve descripción del factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="30745-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="30745-108">Impacto en el dispositivo: Qué tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="30745-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="30745-109">Criterios de calidad: Cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="30745-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="30745-110">Cómo medir: métodos para medir (o experimentar) el problema.</span><span class="sxs-lookup"><span data-stu-id="30745-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="30745-111">Recomendaciones: Resumen de los enfoques para proporcionar una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="30745-112">Recursos: recursos de desarrollador y diseño relevantes que son útiles para crear mejores experiencias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="30745-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="30745-113">Frame rate</span></span>

<span data-ttu-id="30745-114">La velocidad de fotogramas es el primer pilar de estabilidad del holograma y la comodidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="30745-115">La velocidad de fotogramas por debajo de los objetivos recomendados puede hacer que los hologramas parezcan vibrantes, lo que afecta negativamente a la increíble potencia de la experiencia y, potencialmente, a la fatiga ocular.</span><span class="sxs-lookup"><span data-stu-id="30745-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="30745-116">La velocidad de fotogramas de destino para su experiencia en los auriculares de la realidad mixta de Windows será de 60Hz o 90Hz, según los equipos compatibles con Windows Mixed Reality que desee admitir.</span><span class="sxs-lookup"><span data-stu-id="30745-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="30745-117">Para HoloLens, la velocidad de fotogramas de destino es 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="30745-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-118">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-121">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-121">✔️</span></span></td>
        <td><span data-ttu-id="30745-122">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-123">Quality criteria</span></span>

|  <span data-ttu-id="30745-124">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-124">Best</span></span>  |  <span data-ttu-id="30745-125">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-125">Meets</span></span> |  <span data-ttu-id="30745-126">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="30745-127">La aplicación cumple de forma coherente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en ultra PCs; y 60fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="30745-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="30745-128">La aplicación tiene caídas de fotogramas intermitentes que no impiden la experiencia básica; o FPS es constantemente inferior al objetivo deseado, pero no impide la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="30745-129">La aplicación está experimentando una caída en la velocidad de fotogramas como promedio cada diez segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="30745-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="30745-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-130">How to measure</span></span>

* <span data-ttu-id="30745-131">El [portal de dispositivos de Windows](using-the-windows-device-portal.md#system-performance) proporciona un gráfico de velocidad de fotogramas en tiempo real en "rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="30745-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="30745-132">Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="30745-133">Vea recursos para obtener un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="30745-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="30745-134">Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras la aplicación se está ejecutando moviendo el encabezado de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="30745-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="30745-135">Si el holograma muestra un movimiento de vibración inesperado, es probable que la velocidad de fotogramas baja o el plano de estabilidad sea la causa.</span><span class="sxs-lookup"><span data-stu-id="30745-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-136">Recommendations</span></span>

* <span data-ttu-id="30745-137">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="30745-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="30745-138">Los cambios que incurren en una caída en la velocidad de fotogramas se deben evaluar y resolver correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="30745-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-140">Documentation</span></span>

* [<span data-ttu-id="30745-141">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="30745-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="30745-142">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="30745-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="30745-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="30745-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="30745-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="30745-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-145">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-146">MRToolkit, pantalla de contador de FPS</span><span class="sxs-lookup"><span data-stu-id="30745-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="30745-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="30745-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="30745-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="30745-148">External references</span></span>

* [<span data-ttu-id="30745-149">Unity, optimizar aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="30745-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="30745-150">Estabilidad de hologramas</span><span class="sxs-lookup"><span data-stu-id="30745-150">Hologram stability</span></span>

<span data-ttu-id="30745-151">Los hologramas estables aumentarán la facilidad de uso y la increíble capacidad de su aplicación, y crearán una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="30745-152">La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de la aplicación y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno.</span><span class="sxs-lookup"><span data-stu-id="30745-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="30745-153">Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, como:</span><span class="sxs-lookup"><span data-stu-id="30745-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="30745-154">Uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="30745-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="30745-155">Distancia a los delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="30745-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="30745-156">Seguimiento</span><span class="sxs-lookup"><span data-stu-id="30745-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-157">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-160">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-161">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-161">Quality criteria</span></span>

|  <span data-ttu-id="30745-162">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-162">Best</span></span>  |  <span data-ttu-id="30745-163">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-163">Meets</span></span> |  <span data-ttu-id="30745-164">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-165">Los hologramas aparecen de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="30745-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="30745-166">El contenido secundario exhibe un movimiento inesperado. o el movimiento inesperado no impide la experiencia general de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="30745-167">El contenido principal del marco exhibe un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="30745-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="30745-168">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-168">How to measure</span></span>

<span data-ttu-id="30745-169">Con el dispositivo y la visualización de la experiencia:</span><span class="sxs-lookup"><span data-stu-id="30745-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="30745-170">Mover el encabezado de lado a lado, si los hologramas muestran un movimiento inesperado, la velocidad de fotogramas baja o la alineación incorrecta del plano de estabilidad al plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="30745-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="30745-171">Desplazarse por los hologramas y el entorno, busque comportamientos como nadar y salto.</span><span class="sxs-lookup"><span data-stu-id="30745-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="30745-172">Este tipo de movimiento probablemente se debe a que el dispositivo no realiza un seguimiento del entorno o a la distancia al delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="30745-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="30745-173">Si hay varios hologramas en el marco, observe el comportamiento de holograma en varias profundidades al mover la posición principal de lado a lado, en caso de que la irregularidad parezca que esto se debe a un plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="30745-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-174">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-174">Recommendations</span></span>

* <span data-ttu-id="30745-175">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="30745-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="30745-176">Use el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="30745-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="30745-177">Siempre representa los hologramas anclados dentro de los 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="30745-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="30745-178">Asegúrese de que el entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="30745-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="30745-179">Diseñe su experiencia para evitar los hologramas en diversos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="30745-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-180">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-181">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-181">Documentation</span></span>

* [<span data-ttu-id="30745-182">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="30745-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="30745-183">Caso práctico, uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="30745-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="30745-184">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="30745-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="30745-185">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="30745-185">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="30745-186">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="30745-186">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="30745-187">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="30745-187">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="30745-188">Marco estacionario de referencia</span><span class="sxs-lookup"><span data-stu-id="30745-188">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-189">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-189">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-190">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="30745-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="30745-191">Posición de hologramas en superficies reales</span><span class="sxs-lookup"><span data-stu-id="30745-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="30745-192">Las alineaciones de los hologramas con objetos físicos (si se prevé que se colocarán en relación con otras) son una indicación clara de la no Unión de los hologramas y del mundo real.</span><span class="sxs-lookup"><span data-stu-id="30745-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="30745-193">La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; por ejemplo, la selección de ubicación de superficie general puede usar el mapa espacial, pero la selección de ubicación más precisa requerirá el uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="30745-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-194">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-197">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-198">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-198">Quality criteria</span></span>

|  <span data-ttu-id="30745-199">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-199">Best</span></span>  |  <span data-ttu-id="30745-200">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-200">Meets</span></span> |  <span data-ttu-id="30745-201">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="30745-202">Los hologramas se alinean a la superficie normalmente en el intervalo de centímetros a pulgadas.</span><span class="sxs-lookup"><span data-stu-id="30745-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="30745-203">Si se requiere más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="30745-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="30745-204">N/D</span><span class="sxs-lookup"><span data-stu-id="30745-204">NA</span></span> | <span data-ttu-id="30745-205">Los hologramas aparecen sin alinear con el objeto de destino físico, ya que separan el plano de la superficie o parecen flotar fuera de la superficie.</span><span class="sxs-lookup"><span data-stu-id="30745-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="30745-206">Si se requiere precisión, los hologramas deben cumplir las especificaciones de proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="30745-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-207">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-207">How to measure</span></span>

* <span data-ttu-id="30745-208">Los hologramas que se colocan en el mapa espacial no deben parecer drásticamente por encima o por debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="30745-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="30745-209">Los hologramas que requieren una ubicación precisa deben tener algún tipo de sistema de marcadores y calibración que sea preciso para el requisito del escenario.</span><span class="sxs-lookup"><span data-stu-id="30745-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-210">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-210">Recommendations</span></span>

* <span data-ttu-id="30745-211">El mapa espacial resulta útil para colocar objetos en superficies cuando no se requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="30745-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="30745-212">Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="30745-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="30745-213">Considere la posibilidad de dividir los hologramas extra grandes en partes lógicas y alinear cada parte en la superficie.</span><span class="sxs-lookup"><span data-stu-id="30745-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="30745-214">La Interpupillary distancia establecida correctamente (IPD) también puede afectar a la alineación de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="30745-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="30745-215">Configure siempre HoloLens en el del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-216">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-217">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-217">Documentation</span></span>

* [<span data-ttu-id="30745-218">Colocación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="30745-218">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="30745-219">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="30745-219">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="30745-220">Procedimientos recomendados para los anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="30745-220">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="30745-221">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="30745-221">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="30745-222">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-222">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="30745-223">Información general sobre el desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="30745-223">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-224">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-224">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-225">Kit de herramientas de MR, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="30745-225">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="30745-226">Kit complementario MR, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="30745-226">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="30745-227">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="30745-227">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="30745-228">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="30745-228">External references</span></span>

* [<span data-ttu-id="30745-229">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="30745-229">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="30745-230">Ver la zona de confort</span><span class="sxs-lookup"><span data-stu-id="30745-230">Viewing zone of comfort</span></span>

<span data-ttu-id="30745-231">Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades.</span><span class="sxs-lookup"><span data-stu-id="30745-231">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="30745-232">Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se fijan a una distancia óptica aproximadamente a 2,0 m del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-232">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="30745-233">Una profundidad de contenido incorrecta puede conducir a la molestia visual o a la fatiga.</span><span class="sxs-lookup"><span data-stu-id="30745-233">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-234">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-234">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-237">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-237">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-238">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-238">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="30745-239">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-239">Best</span></span> </td><td><ul>
<li><span data-ttu-id="30745-240">Coloque el contenido en 2m.</span><span class="sxs-lookup"><span data-stu-id="30745-240">Place content at 2m.</span></span></li><li><span data-ttu-id="30745-241">Cuando los hologramas no se pueden colocar en 2m y no se pueden evitar conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m.</span><span class="sxs-lookup"><span data-stu-id="30745-241">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="30745-242">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).</span><span class="sxs-lookup"><span data-stu-id="30745-242">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="30745-243">A menos que el escenario no requiera específicamente, se debe implementar un plano de recorte con fadeout a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="30745-243">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="30745-244">En los casos en los que se requiere una observación más detallada de un holograma de motionless, el contenido no debe estar más cerca que 50CM.</span><span class="sxs-lookup"><span data-stu-id="30745-244">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="30745-245">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-245">Meets</span></span></td><td> <span data-ttu-id="30745-246">El contenido está dentro de la guía de visualización y movimiento, pero se usa inadecuadamente o no se usa el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="30745-246">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="30745-247">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-247">Fail</span></span> </td><td> <span data-ttu-id="30745-248">El contenido se presenta demasiado cerca (normalmente &lt; 1,25 m o &lt; 50CM para los hologramas estacionales que requieren una observación más detallada).</span><span class="sxs-lookup"><span data-stu-id="30745-248">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="30745-249">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-249">How to measure</span></span>

* <span data-ttu-id="30745-250">Normalmente, el contenido debe ser de 2 m, pero no más cercano a 1,25 o superior a 5 m.</span><span class="sxs-lookup"><span data-stu-id="30745-250">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="30745-251">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en. 85CM con fadeout de contenido que empieza en 1m.</span><span class="sxs-lookup"><span data-stu-id="30745-251">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="30745-252">Acerque el contenido y observe el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="30745-252">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="30745-253">El contenido estacionario no debe estar más cerca de 50CM.</span><span class="sxs-lookup"><span data-stu-id="30745-253">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-254">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-254">Recommendations</span></span>

* <span data-ttu-id="30745-255">Diseñe el contenido para obtener la distancia de visualización óptima de 2 m.</span><span class="sxs-lookup"><span data-stu-id="30745-255">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="30745-256">Establezca la distancia de representación de recorte en 85cm con fadeout de contenido a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="30745-256">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="30745-257">En el caso de los hologramas estacionales que necesitan una visualización más estrecha, el plano de recorte no debe estar más cerca de 30cm y fadeout debe iniciar al menos 10cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="30745-257">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-258">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-258">Resources</span></span>

* [<span data-ttu-id="30745-259">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="30745-259">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="30745-260">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-260">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="30745-261">Experimentación con escala</span><span class="sxs-lookup"><span data-stu-id="30745-261">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="30745-262">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="30745-262">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="30745-263">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="30745-263">Depth switching</span></span>

<span data-ttu-id="30745-264">Sin tener en cuenta los problemas de la zona de confort, las demandas del usuario a cambiar con frecuencia o rapidez entre los objetos cercanos y lejanos (incluidos los hologramas y el contenido del mundo real) pueden conducir a la fatiga oculomotor y a la molestia general.</span><span class="sxs-lookup"><span data-stu-id="30745-264">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-265">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-265">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-268">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-268">✔️</span></span></td>
        <td><span data-ttu-id="30745-269">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-269">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-270">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-270">Quality criteria</span></span>

|  <span data-ttu-id="30745-271">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-271">Best</span></span>  |  <span data-ttu-id="30745-272">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-272">Meets</span></span> |  <span data-ttu-id="30745-273">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-273">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-274">Cambio de profundidad limitado o natural que no hace que el usuario se recentre sin ningún problema.</span><span class="sxs-lookup"><span data-stu-id="30745-274">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="30745-275">Cambio de profundidad abrupta: este es el núcleo y está diseñado en la experiencia de la aplicación, o en el modificador de profundidad abrupta causado por contenido real inesperado.</span><span class="sxs-lookup"><span data-stu-id="30745-275">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="30745-276">Conmutador de profundidad coherente o cambio de profundidad brusco que no es necesario ni básico para la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-276">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-277">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-277">How to measure</span></span>

* <span data-ttu-id="30745-278">Si la aplicación requiere que el usuario cambie de forma constante y/o repentinamente el foco de profundidad, hay un problema de conmutación de profundidad.</span><span class="sxs-lookup"><span data-stu-id="30745-278">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-279">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-279">Recommendations</span></span>

* <span data-ttu-id="30745-280">Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="30745-280">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="30745-281">Esto evitará la fatiga oculomotor y el movimiento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="30745-281">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-282">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-282">Resources</span></span>

* [<span data-ttu-id="30745-283">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="30745-283">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="30745-284">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-284">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="30745-285">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="30745-285">Use of spatial sound</span></span>

<span data-ttu-id="30745-286">En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno.</span><span class="sxs-lookup"><span data-stu-id="30745-286">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="30745-287">El uso de un sonido espacial en una aplicación permite a los desarrolladores colocar los sonidos de forma convincente en un espacio tridimensional (esfera) alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-287">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="30745-288">Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-288">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="30745-289">El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="30745-289">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-290">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-290">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-293">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-293">✔️</span></span></td>
        <td><span data-ttu-id="30745-294">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-294">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-295">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-295">Quality criteria</span></span>

|  <span data-ttu-id="30745-296">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-296">Best</span></span>  |  <span data-ttu-id="30745-297">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-297">Meets</span></span> |  <span data-ttu-id="30745-298">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-298">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-299">El sonido está espacial lógicamente y la experiencia de usuario usa correctamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="30745-299">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="30745-300">El sonido es natural y relevante para los objetos y se normaliza en el escenario.</span><span class="sxs-lookup"><span data-stu-id="30745-300">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="30745-301">El audio espacial se utiliza de forma adecuada para aumentar la capacidad de respuesta, pero falta como medio para ayudar con los comentarios de los usuarios y la detectabilidad.</span><span class="sxs-lookup"><span data-stu-id="30745-301">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="30745-302">El sonido no está espacialmente como se esperaba o falta de sonido para ayudar al usuario dentro de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-302">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="30745-303">O el audio espacial no se consideró ni usó en el diseño del escenario.</span><span class="sxs-lookup"><span data-stu-id="30745-303">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-304">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-304">How to measure</span></span>

* <span data-ttu-id="30745-305">En general, los sonidos relevantes deben emitirse desde los hologramas de destino (por ejemplo, el sonido de corteza procedente de holográfica Dog).</span><span class="sxs-lookup"><span data-stu-id="30745-305">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="30745-306">Deben usarse señales sonoras en toda la experiencia del usuario para ayudar al usuario a realizar comentarios o a conocer las acciones que se encuentran fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="30745-306">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-307">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-307">Recommendations</span></span>

* <span data-ttu-id="30745-308">Use el audio espacial para ayudar con la detección de objetos y las interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-308">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="30745-309">Los sonidos reales funcionan mejor que la síntesis o el sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="30745-309">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="30745-310">La mayoría de los sonidos deben ser espaciales.</span><span class="sxs-lookup"><span data-stu-id="30745-310">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="30745-311">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="30745-311">Avoid invisible emitters.</span></span>
* <span data-ttu-id="30745-312">Evite el enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="30745-312">Avoid spatial masking.</span></span>
* <span data-ttu-id="30745-313">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="30745-313">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-314">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-314">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-315">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-315">Documentation</span></span>

* [<span data-ttu-id="30745-316">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="30745-316">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="30745-317">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="30745-317">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="30745-318">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-318">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="30745-319">Caso práctico, sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="30745-319">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="30745-320">Caso práctico, uso de sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="30745-320">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-321">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-321">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-322">MRToolkit, audio espacial</span><span class="sxs-lookup"><span data-stu-id="30745-322">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="30745-323">Centrarse en los límites de trama holográfica (hipertema)</span><span class="sxs-lookup"><span data-stu-id="30745-323">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="30745-324">Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="30745-324">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="30745-325">Mitigar el efecto de los límites de los hipertextos implica un diseño minucioso de la escala y el contexto del contenido, el uso de audio espacial, los sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-325">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="30745-326">Si se realiza correctamente, el usuario sentirá menos el límite de los límites de los subprocesos, a la vez que tiene una experiencia de aplicación cómoda.</span><span class="sxs-lookup"><span data-stu-id="30745-326">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-327">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-327">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-330">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-330">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-331">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-331">Quality criteria</span></span>

|  <span data-ttu-id="30745-332">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-332">Best</span></span>  |  <span data-ttu-id="30745-333">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-333">Meets</span></span> |  <span data-ttu-id="30745-334">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-334">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-335">El usuario nunca pierde el contexto y se siente cómodo.</span><span class="sxs-lookup"><span data-stu-id="30745-335">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="30745-336">Se proporciona asistencia contextual para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="30745-336">Context assistance is provided for large objects.</span></span> <span data-ttu-id="30745-337">Se proporcionan instrucciones de detección y visualización para los objetos que se encuentran fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="30745-337">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="30745-338">En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="30745-338">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="30745-339">El usuario nunca pierde el contexto, pero es posible que se requiera movimiento de cuello adicional en situaciones limitadas.</span><span class="sxs-lookup"><span data-stu-id="30745-339">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="30745-340">En situaciones limitadas, la escala hace que los hologramas interrumpan el fotograma vertical u horizontal, lo que produce un movimiento de cuello para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="30745-340">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="30745-341">Es necesario que el usuario pierda el contexto o el movimiento de cuello coherente para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="30745-341">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="30745-342">No hay ninguna guía de contexto para objetos holográficas grandes, el movimiento de objetos es fácil de perder fuera del marco sin ninguna guía de detección, o bien un holograma alto requiere un movimiento de cuello normal para verlo.</span><span class="sxs-lookup"><span data-stu-id="30745-342">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-343">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-343">How to measure</span></span>

* <span data-ttu-id="30745-344">El contexto de un holograma (grande) se pierde o no se entiende debido a que se recortan en los límites.</span><span class="sxs-lookup"><span data-stu-id="30745-344">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="30745-345">La ubicación de los hologramas es difícil de encontrar debido a la falta de directores de atención o al contenido que mueve y sale rápidamente del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="30745-345">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="30745-346">El escenario requiere un movimiento de cabezal normal y repetitivo hacia arriba y hacia abajo para ver por completo un holograma que dé lugar a una fatiga del cuello.</span><span class="sxs-lookup"><span data-stu-id="30745-346">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-347">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-347">Recommendations</span></span>

* <span data-ttu-id="30745-348">Comience la experiencia con objetos pequeños que se ajusten al objeto de subproceso y, a continuación, transición con indicaciones visuales a versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="30745-348">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="30745-349">Use los directores de audio y atención espaciales para ayudar al usuario a encontrar contenido que está fuera del hipermismo.</span><span class="sxs-lookup"><span data-stu-id="30745-349">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="30745-350">En la medida de lo posible, evite los hologramas que recortan verticalmente el hipernivel.</span><span class="sxs-lookup"><span data-stu-id="30745-350">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="30745-351">Proporcionar al usuario orientación en la aplicación para obtener la mejor ubicación de visualización.</span><span class="sxs-lookup"><span data-stu-id="30745-351">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-352">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-352">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-353">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-353">Documentation</span></span>

* [<span data-ttu-id="30745-354">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="30745-354">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="30745-355">Caso práctico, aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="30745-355">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="30745-356">Escala de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="30745-356">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="30745-357">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="30745-357">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="30745-358">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="30745-358">External references</span></span>

* [<span data-ttu-id="30745-359">Gran cantidad de ADO sobre el visual</span><span class="sxs-lookup"><span data-stu-id="30745-359">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="30745-360">El contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="30745-360">Content reacts to user position</span></span>

<span data-ttu-id="30745-361">Los hologramas deben reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales".</span><span class="sxs-lookup"><span data-stu-id="30745-361">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="30745-362">Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario sea estacional y adaptarse al movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-362">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="30745-363">El diseño de una aplicación que se adapta correctamente a la posición del usuario creará una experiencia más increíble y facilitará su uso.</span><span class="sxs-lookup"><span data-stu-id="30745-363">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-364">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-364">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-367">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-367">✔️</span></span></td>
        <td><span data-ttu-id="30745-368">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-368">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-369">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-369">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="30745-370">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-370">Best</span></span> </td><td> <span data-ttu-id="30745-371">El contenido y la interfaz de usuario se adaptan a las posiciones de los usuarios, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito de movimiento esperado</span><span class="sxs-lookup"><span data-stu-id="30745-371">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="30745-372">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-372">Meets</span></span> </td><td> <span data-ttu-id="30745-373">La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave que requiere que el usuario ajuste su posición.</span><span class="sxs-lookup"><span data-stu-id="30745-373">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="30745-374">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-374">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="30745-375">Los elementos de la interfaz de usuario se pierden o se bloquean durante el movimiento, lo que provoca que el usuario vuelva a los controles (o los busque) de una misma.</span><span class="sxs-lookup"><span data-stu-id="30745-375">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="30745-376">Los elementos de la interfaz de usuario limitan la vista del contenido principal.</span><span class="sxs-lookup"><span data-stu-id="30745-376">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="30745-377">El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el momento, especialmente con elementos de interfaz <a href="../../design/billboarding-and-tag-along.md">de usuario de etiquetas</a> .</span><span class="sxs-lookup"><span data-stu-id="30745-377">UI movement is not optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="30745-378">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-378">How to measure</span></span>

* <span data-ttu-id="30745-379">Todas las medidas deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="30745-379">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="30745-380">Aunque el movimiento del usuario variará, no intente engañar a la aplicación con un movimiento de usuario extremo.</span><span class="sxs-lookup"><span data-stu-id="30745-380">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="30745-381">En el caso de los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-381">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="30745-382">Por ejemplo, si el usuario está viendo y recorriendo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="30745-382">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-383">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-383">Recommendations</span></span>

* <span data-ttu-id="30745-384">El usuario es la cámara y controla el movimiento.</span><span class="sxs-lookup"><span data-stu-id="30745-384">The user is the camera and they control the movement.</span></span> <span data-ttu-id="30745-385">Dejar que se controlen.</span><span class="sxs-lookup"><span data-stu-id="30745-385">Let them drive.</span></span>
* <span data-ttu-id="30745-386">Considere la posibilidad de mostrar los sistemas de texto y de menú que, de otro modo, podrían quedar bloqueados o desconocidos si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="30745-386">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="30745-387">Use la etiqueta junto con el contenido que debe seguir al usuario y, al mismo tiempo, permitir que el usuario vea lo que hay delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="30745-387">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-388">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-388">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-389">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-389">Documentation</span></span>

* [<span data-ttu-id="30745-390">Diseño de la interacción</span><span class="sxs-lookup"><span data-stu-id="30745-390">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="30745-391">Color, claro y material</span><span class="sxs-lookup"><span data-stu-id="30745-391">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="30745-392">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="30745-392">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="30745-393">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="30745-393">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="30745-394">Automovimiento y locomoción del usuario</span><span class="sxs-lookup"><span data-stu-id="30745-394">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="30745-395">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="30745-395">Input interaction clarity</span></span>

<span data-ttu-id="30745-396">La claridad de la interacción de entrada es fundamental para el uso de una aplicación e incluye la coherencia de entrada, la capacidad de enfoque, la detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="30745-396">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="30745-397">El usuario debe poder usar las interacciones comunes de toda la plataforma sin tener que reaprender.</span><span class="sxs-lookup"><span data-stu-id="30745-397">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="30745-398">Si la aplicación tiene una entrada personalizada, debe comunicarse claramente y mostrarse.</span><span class="sxs-lookup"><span data-stu-id="30745-398">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-399">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-399">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-402">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-402">✔️</span></span></td>
        <td><span data-ttu-id="30745-403">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-403">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-404">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-404">Quality criteria</span></span>

|  <span data-ttu-id="30745-405">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-405">Best</span></span>  |  <span data-ttu-id="30745-406">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-406">Meets</span></span> |  <span data-ttu-id="30745-407">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-407">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-408">Los métodos de interacción de entrada son coherentes con las [instrucciones](../../design/interaction-fundamentals.md)proporcionadas por Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="30745-408">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="30745-409">Cualquier entrada personalizada no debe ser redundante con entrada estándar (en lugar de usar la interacción estándar) y se debe comunicar y demostrar claramente al usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-409">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="30745-410">Similar a lo mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="30745-410">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="30745-411">El usuario puede seguir logrando el objetivo y el progreso a través de la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-411">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="30745-412">Es difícil comprender la asignación de botones o métodos de entrada.</span><span class="sxs-lookup"><span data-stu-id="30745-412">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="30745-413">La entrada está muy personalizada, no es compatible con la entrada estándar, no hay instrucciones o probablemente cause problemas de fatiga y confort.</span><span class="sxs-lookup"><span data-stu-id="30745-413">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-414">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-414">How to measure</span></span>

* <span data-ttu-id="30745-415">La aplicación usa [métodos de entrada estándar](../../design/interaction-fundamentals.md) coherentes.</span><span class="sxs-lookup"><span data-stu-id="30745-415">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="30745-416">Si la aplicación tiene una entrada personalizada, se comunica claramente mediante:</span><span class="sxs-lookup"><span data-stu-id="30745-416">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="30745-417">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="30745-417">First-run experience</span></span>
* <span data-ttu-id="30745-418">Pantallas de introducción</span><span class="sxs-lookup"><span data-stu-id="30745-418">Introductory screens</span></span>
* <span data-ttu-id="30745-419">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="30745-419">Tooltips</span></span>
* <span data-ttu-id="30745-420">Asesor manual</span><span class="sxs-lookup"><span data-stu-id="30745-420">Hand coach</span></span>
* <span data-ttu-id="30745-421">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="30745-421">Help section</span></span>
* <span data-ttu-id="30745-422">Voice over</span><span class="sxs-lookup"><span data-stu-id="30745-422">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-423">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-423">Recommendations</span></span>

* <span data-ttu-id="30745-424">Utilice los métodos de entrada estándar siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="30745-424">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="30745-425">Proporcione demostraciones, tutoriales e información sobre herramientas para los métodos de entrada no estándar.</span><span class="sxs-lookup"><span data-stu-id="30745-425">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="30745-426">Use un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-426">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-427">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-427">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-428">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-428">Documentation</span></span>

* [<span data-ttu-id="30745-429">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="30745-429">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="30745-430">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="30745-430">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="30745-431">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="30745-431">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="30745-432">Cursores</span><span class="sxs-lookup"><span data-stu-id="30745-432">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="30745-433">Confort y mira</span><span class="sxs-lookup"><span data-stu-id="30745-433">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="30745-434">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="30745-434">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="30745-435">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="30745-435">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="30745-436">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="30745-436">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="30745-437">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-437">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="30745-438">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-438">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="30745-439">Gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-439">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="30745-440">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-440">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="30745-441">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="30745-441">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="30745-442">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="30745-442">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="30745-443">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="30745-443">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="30745-444">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="30745-444">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-445">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-445">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-446">Caso práctico: el logro de más informática personal</span><span class="sxs-lookup"><span data-stu-id="30745-446">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="30745-447">Estudio de conversión: aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="30745-447">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="30745-448">Aplicación de ejemplo: tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="30745-448">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="30745-449">Aplicación de ejemplo: módulo lunar</span><span class="sxs-lookup"><span data-stu-id="30745-449">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="30745-450">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="30745-450">Interactable objects</span></span>

<span data-ttu-id="30745-451">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="30745-451">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="30745-452">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="30745-452">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="30745-453">Cualquier elemento puede ser un objeto interactuable que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="30745-453">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="30745-454">Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="30745-454">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="30745-455">Independientemente del formulario, los objetos interactivos deben ser claramente reconocibles por el usuario a través de las indicaciones de audio y visual.</span><span class="sxs-lookup"><span data-stu-id="30745-455">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-456">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-456">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-459">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-459">✔️</span></span></td>
        <td><span data-ttu-id="30745-460">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-460">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-461">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-461">Quality criteria</span></span>

|  <span data-ttu-id="30745-462">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-462">Best</span></span>  |  <span data-ttu-id="30745-463">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-463">Meets</span></span> |  <span data-ttu-id="30745-464">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-464">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-465">Independientemente del formulario, los objetos interactuables se pueden reconocer a través de las indicaciones de audio y visual en tres Estados: inactivo, dirigido y seleccionado.</span><span class="sxs-lookup"><span data-stu-id="30745-465">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="30745-466">"Lo veo, por ejemplo, está claro y se usa de forma coherente en toda la experiencia.</span><span class="sxs-lookup"><span data-stu-id="30745-466">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="30745-467">Los objetos se escalan y distribuyen para permitir la finalización de errores de forma gratuita.</span><span class="sxs-lookup"><span data-stu-id="30745-467">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="30745-468">El usuario puede reconocer objetos como interactivos a través de comentarios de audio o visuales, y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="30745-468">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="30745-469">No se proporcionan indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="30745-469">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="30745-470">Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="30745-470">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-471">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-471">How to measure</span></span>

* <span data-ttu-id="30745-472">Los objetos interactuables son reconocibles como ' interactuable '; incluir botones, menús y contenido específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30745-472">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="30745-473">Como regla general, debe haber una indicación visual y de audio cuando el destino es objetos interactivos.</span><span class="sxs-lookup"><span data-stu-id="30745-473">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-474">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-474">Recommendations</span></span>

* <span data-ttu-id="30745-475">Use comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="30745-475">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="30745-476">Los comentarios visuales deben diferenciarse en cada estado de entrada (inactivo, dirigido, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="30745-476">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="30745-477">Los objetos que se pueden interactuar deben escalarse y colocarse para los destinos sin errores.</span><span class="sxs-lookup"><span data-stu-id="30745-477">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="30745-478">Los objetos interactuables agrupados (por ejemplo, una barra de menús o una lista) deben tener el espaciado adecuado para el destino.</span><span class="sxs-lookup"><span data-stu-id="30745-478">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="30745-479">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave Command ("vea esto, dígalo")</span><span class="sxs-lookup"><span data-stu-id="30745-479">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="30745-480">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-480">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-481">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-481">Documentation</span></span>

* [<span data-ttu-id="30745-482">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="30745-482">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="30745-483">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="30745-483">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="30745-484">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="30745-484">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="30745-485">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="30745-485">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-486">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-486">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-487">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="30745-487">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="30745-488">Detección de salas</span><span class="sxs-lookup"><span data-stu-id="30745-488">Room scanning</span></span>

<span data-ttu-id="30745-489">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="30745-489">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="30745-490">La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="30745-490">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="30745-491">Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="30745-491">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="30745-492">Si es necesario que el usuario analice el entorno, debe proporcionar instrucciones claras durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="30745-492">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-493">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-493">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-496">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-496">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-497">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-497">Quality criteria</span></span>

|  <span data-ttu-id="30745-498">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-498">Best</span></span>  |  <span data-ttu-id="30745-499">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-499">Meets</span></span> |  <span data-ttu-id="30745-500">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-500">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-501">Visualización de la malla espacial indique a los usuarios que el análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="30745-501">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="30745-502">El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="30745-502">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="30745-503">Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y que no se proporcione información de progreso.</span><span class="sxs-lookup"><span data-stu-id="30745-503">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="30745-504">Ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="30745-504">No visualization of mesh.</span></span> <span data-ttu-id="30745-505">No se proporciona información de orientación al usuario sobre dónde buscar, o Cuándo se inicia o se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="30745-505">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="30745-506">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-506">How to measure</span></span>

* <span data-ttu-id="30745-507">Durante un examen de habitación necesario, se proporciona orientación visual y de audio que indica dónde buscar y cuándo iniciar y detener el examen.</span><span class="sxs-lookup"><span data-stu-id="30745-507">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-508">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-508">Recommendations</span></span>

* <span data-ttu-id="30745-509">Indique la cantidad del volumen total de los usuarios que debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="30745-509">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="30745-510">Comunicarse cuando el examen se inicia y se detiene, como un indicador de progreso.</span><span class="sxs-lookup"><span data-stu-id="30745-510">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="30745-511">Use una visualización de la malla durante el examen.</span><span class="sxs-lookup"><span data-stu-id="30745-511">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="30745-512">Proporcione guías de audio y visual para animar al usuario a buscar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="30745-512">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="30745-513">Informe al usuario de dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="30745-513">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="30745-514">En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="30745-514">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-515">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-515">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="30745-516">Documentación</span><span class="sxs-lookup"><span data-stu-id="30745-516">Documentation</span></span>

* [<span data-ttu-id="30745-517">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="30745-517">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="30745-518">Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="30745-518">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="30745-519">Caso práctico: diseño de sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="30745-519">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="30745-520">Caso práctico: creación de una experiencia envolvente en fragmentos</span><span class="sxs-lookup"><span data-stu-id="30745-520">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="30745-521">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="30745-521">Tools and tutorials</span></span>

* [<span data-ttu-id="30745-522">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="30745-522">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="30745-523">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="30745-523">Directional indicators</span></span>

<span data-ttu-id="30745-524">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista o ocluidos por objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="30745-524">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="30745-525">Una aplicación bien diseñada facilitará a los usuarios la búsqueda de contenido no visible.</span><span class="sxs-lookup"><span data-stu-id="30745-525">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="30745-526">Los indicadores direccionales avisan a un usuario de contenido importante y proporcionan orientación sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-526">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="30745-527">Las instrucciones para el contenido no visible pueden adoptar la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="30745-527">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-528">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-528">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-531">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-531">✔️</span></span></td>
        <td><span data-ttu-id="30745-532">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-532">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-533">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-533">Quality criteria</span></span>

|  <span data-ttu-id="30745-534">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-534">Best</span></span>  |  <span data-ttu-id="30745-535">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-535">Meets</span></span> |  <span data-ttu-id="30745-536">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-536">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-537">Las guías de audio y visual guían directamente al usuario al contenido relevante fuera del campo de vista.</span><span class="sxs-lookup"><span data-stu-id="30745-537">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="30745-538">Una flecha o algún indicador que apunta al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="30745-538">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="30745-539">El contenido relevante está fuera del campo de vista y no se proporciona ninguna guía de ubicación para el usuario.</span><span class="sxs-lookup"><span data-stu-id="30745-539">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="30745-540">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-540">How to measure</span></span>

* <span data-ttu-id="30745-541">El contenido relevante fuera del campo de vista de usuario se detecta mediante señales de audio o visual.</span><span class="sxs-lookup"><span data-stu-id="30745-541">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-542">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-542">Recommendations</span></span>

* <span data-ttu-id="30745-543">Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="30745-543">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="30745-544">En muchos casos, se prefiere una guía visual directa a las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="30745-544">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="30745-545">Los indicadores direccionales no se deben integrar en el cursor.</span><span class="sxs-lookup"><span data-stu-id="30745-545">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-546">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-546">Resources</span></span>

* [<span data-ttu-id="30745-547">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="30745-547">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="30745-548">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="30745-548">Data loading</span></span>

<span data-ttu-id="30745-549">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="30745-549">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="30745-550">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo puede ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="30745-550">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="30745-551">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="30745-551">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30745-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="30745-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30745-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30745-554">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-554">✔️</span></span></td>
        <td><span data-ttu-id="30745-555">✔️</span><span class="sxs-lookup"><span data-stu-id="30745-555">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="30745-556">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="30745-556">Quality criteria</span></span>

|  <span data-ttu-id="30745-557">Óptima</span><span class="sxs-lookup"><span data-stu-id="30745-557">Best</span></span>  |  <span data-ttu-id="30745-558">Reúne</span><span class="sxs-lookup"><span data-stu-id="30745-558">Meets</span></span> |  <span data-ttu-id="30745-559">Suspenso</span><span class="sxs-lookup"><span data-stu-id="30745-559">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="30745-560">Indicador visual animado, en forma de una barra de progreso o un anillo, que muestra el progreso durante cualquier carga o procesamiento de datos.</span><span class="sxs-lookup"><span data-stu-id="30745-560">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="30745-561">El indicador visual proporciona instrucciones sobre cuánto tiempo puede ser la espera.</span><span class="sxs-lookup"><span data-stu-id="30745-561">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="30745-562">Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="30745-562">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="30745-563">No hay ningún indicador de carga de datos o de proceso para que la tarea tarde más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="30745-563">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="30745-564">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="30745-564">How to measure</span></span>

* <span data-ttu-id="30745-565">Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="30745-565">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="30745-566">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="30745-566">Recommendations</span></span>

* <span data-ttu-id="30745-567">Proporcionar un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se haya detenido o bloqueado.</span><span class="sxs-lookup"><span data-stu-id="30745-567">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="30745-568">Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="30745-568">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="30745-569">Recursos</span><span class="sxs-lookup"><span data-stu-id="30745-569">Resources</span></span>

* [<span data-ttu-id="30745-570">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="30745-570">Displaying progress</span></span>](../../design/progress.md)
