---
title: Criterios de calidad de aplicaciones
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: Criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 3f6752c0a15ae7db21be1f4a6d2843339ab28a5c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581261"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="7e385-104">Criterios de calidad de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-104">App quality criteria</span></span>

<span data-ttu-id="7e385-105">En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="7e385-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="7e385-106">Para cada factor, se proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="7e385-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="7e385-107">Información general: breve descripción del factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="7e385-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="7e385-108">Impacto en el dispositivo: Qué tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="7e385-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="7e385-109">Criterios de calidad: Cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="7e385-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="7e385-110">Cómo medir: métodos para medir (o experimentar) el problema.</span><span class="sxs-lookup"><span data-stu-id="7e385-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="7e385-111">Recomendaciones: Resumen de los enfoques para proporcionar una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="7e385-112">Recursos: recursos de desarrollador y diseño relevantes que son útiles para crear mejores experiencias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="7e385-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="7e385-113">Frame rate</span></span>

<span data-ttu-id="7e385-114">La velocidad de fotogramas es el primer pilar de estabilidad del holograma y la comodidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="7e385-115">La velocidad de fotogramas por debajo de los objetivos recomendados puede hacer que los hologramas parezcan vibrantes, lo que afecta negativamente a la increíble potencia de la experiencia y, potencialmente, a la fatiga ocular.</span><span class="sxs-lookup"><span data-stu-id="7e385-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="7e385-116">La velocidad de fotogramas de destino para su experiencia en los auriculares con micrófonos de Windows Mixed Reality es de 60 Hz o 90 Hz, en función de los equipos compatibles con Windows Mixed Reality que admita.</span><span class="sxs-lookup"><span data-stu-id="7e385-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="7e385-117">En el caso de HoloLens, la velocidad de fotogramas de destino es de 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="7e385-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-118">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-121">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-121">✔️</span></span></td>
        <td><span data-ttu-id="7e385-122">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-123">Quality criteria</span></span>

|  <span data-ttu-id="7e385-124">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-124">Best</span></span>  |  <span data-ttu-id="7e385-125">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-125">Meets</span></span> |  <span data-ttu-id="7e385-126">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="7e385-127">La aplicación cumple de forma coherente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60 fps en HoloLens; 90 FPS en ultra PC; y 60 fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="7e385-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="7e385-128">La aplicación tiene caídas de fotogramas intermitentes que no impiden la experiencia principal, o bien FPS es constantemente inferior al objetivo deseado, pero no impide la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="7e385-129">La aplicación está experimentando una caída en la velocidad de fotogramas como promedio cada 10 segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="7e385-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="7e385-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-130">How to measure</span></span>

* <span data-ttu-id="7e385-131">El [portal de dispositivos de Windows](using-the-windows-device-portal.md#system-performance) proporciona un gráfico de velocidad de fotogramas en tiempo real en "rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="7e385-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="7e385-132">Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="7e385-133">Vea recursos para obtener un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7e385-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="7e385-134">Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras la aplicación se está ejecutando moviendo el encabezado de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="7e385-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="7e385-135">Si el holograma muestra un movimiento de vibración inesperado, es probable que la velocidad de fotogramas baja o el plano de estabilidad sea la causa.</span><span class="sxs-lookup"><span data-stu-id="7e385-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-136">Recommendations</span></span>

* <span data-ttu-id="7e385-137">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="7e385-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="7e385-138">Los cambios que incurren en una caída en la velocidad de fotogramas se deben evaluar y resolver correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="7e385-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-140">Documentation</span></span>

* [<span data-ttu-id="7e385-141">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="7e385-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="7e385-142">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="7e385-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="7e385-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="7e385-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="7e385-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-145">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-146">Kit de herramientas de realidad mixta, pantalla de contador de FPS</span><span class="sxs-lookup"><span data-stu-id="7e385-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="7e385-147">Kit de herramientas de realidad mixta, sombreadores</span><span class="sxs-lookup"><span data-stu-id="7e385-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="7e385-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="7e385-148">External references</span></span>

* [<span data-ttu-id="7e385-149">Unity, optimizar aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="7e385-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="7e385-150">Estabilidad de hologramas</span><span class="sxs-lookup"><span data-stu-id="7e385-150">Hologram stability</span></span>

<span data-ttu-id="7e385-151">Los hologramas estables aumentarán la facilidad de uso y la increíble capacidad de su aplicación, y crearán una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="7e385-152">La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de la aplicación y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno.</span><span class="sxs-lookup"><span data-stu-id="7e385-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="7e385-153">Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, como:</span><span class="sxs-lookup"><span data-stu-id="7e385-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="7e385-154">Uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="7e385-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="7e385-155">Distancia a los delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="7e385-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="7e385-156">Seguimiento</span><span class="sxs-lookup"><span data-stu-id="7e385-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-157">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-160">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-161">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-161">Quality criteria</span></span>

|  <span data-ttu-id="7e385-162">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-162">Best</span></span>  |  <span data-ttu-id="7e385-163">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-163">Meets</span></span> |  <span data-ttu-id="7e385-164">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-165">Los hologramas aparecen de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="7e385-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="7e385-166">El contenido secundario muestra el movimiento inesperado. o el movimiento inesperado no impide la experiencia general de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="7e385-167">El contenido principal de Frame muestra un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="7e385-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="7e385-168">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-168">How to measure</span></span>

<span data-ttu-id="7e385-169">Con el dispositivo y la visualización de la experiencia:</span><span class="sxs-lookup"><span data-stu-id="7e385-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="7e385-170">Mueva el dedo de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="7e385-170">Move your head from side to side.</span></span> <span data-ttu-id="7e385-171">Si los hologramas muestran un movimiento inesperado, la velocidad de fotogramas baja o la alineación incorrecta del plano de estabilidad al plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="7e385-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="7e385-172">Desplazarse por los hologramas y el entorno, busque comportamientos como nadar y salto.</span><span class="sxs-lookup"><span data-stu-id="7e385-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="7e385-173">Este tipo de movimiento probablemente se debe a que el dispositivo no realiza un seguimiento del entorno o a la distancia al delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="7e385-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="7e385-174">Si hay varios hologramas en el marco, observe el comportamiento de holograma en varias profundidades al mover la posición principal de lado a lado, en caso de que la irregularidad parezca que esto se debe a un plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="7e385-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-175">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-175">Recommendations</span></span>

* <span data-ttu-id="7e385-176">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="7e385-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="7e385-177">Use el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="7e385-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="7e385-178">Siempre representa los hologramas anclados dentro de los 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="7e385-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="7e385-179">Asegúrese de que el entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="7e385-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="7e385-180">Diseñe su experiencia para evitar los hologramas en diversos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="7e385-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-181">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-182">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-182">Documentation</span></span>

* [<span data-ttu-id="7e385-183">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="7e385-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="7e385-184">Caso práctico, uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="7e385-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="7e385-185">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="7e385-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="7e385-186">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="7e385-187">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="7e385-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="7e385-188">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="7e385-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="7e385-189">Marco estacionario de referencia</span><span class="sxs-lookup"><span data-stu-id="7e385-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-190">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-190">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-191">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="7e385-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="7e385-192">Posición de hologramas en superficies reales</span><span class="sxs-lookup"><span data-stu-id="7e385-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="7e385-193">Las diferencias de los hologramas con objetos físicos (si se prevé que se colocarán en relación entre sí) son una indicación clara de la no Unión de los hologramas y del mundo real.</span><span class="sxs-lookup"><span data-stu-id="7e385-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="7e385-194">La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; por ejemplo, la selección de ubicación de superficie general puede usar el mapa espacial, pero la selección de ubicación más precisa requerirá el uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="7e385-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-195">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-198">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-199">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-199">Quality criteria</span></span>

|  <span data-ttu-id="7e385-200">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-200">Best</span></span>  |  <span data-ttu-id="7e385-201">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-201">Meets</span></span> |  <span data-ttu-id="7e385-202">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="7e385-203">Los hologramas se alinean a la superficie normalmente en el intervalo de centímetros a pulgadas.</span><span class="sxs-lookup"><span data-stu-id="7e385-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="7e385-204">Si necesita más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="7e385-205">N/D</span><span class="sxs-lookup"><span data-stu-id="7e385-205">NA</span></span> | <span data-ttu-id="7e385-206">Los hologramas aparecen sin alinear con el objeto de destino físico, ya que separan el plano de la superficie o parecen flotar fuera de la superficie.</span><span class="sxs-lookup"><span data-stu-id="7e385-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="7e385-207">Si se requiere precisión, los hologramas deben cumplir las especificaciones de proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="7e385-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-208">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-208">How to measure</span></span>

* <span data-ttu-id="7e385-209">Los hologramas que se colocan en el mapa espacial no deben parecer drásticamente por encima o por debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="7e385-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="7e385-210">Los hologramas que requieren una ubicación precisa deben tener algún tipo de sistema de marcadores y calibración que sea preciso para el requisito del escenario.</span><span class="sxs-lookup"><span data-stu-id="7e385-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-211">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-211">Recommendations</span></span>

* <span data-ttu-id="7e385-212">El mapa espacial resulta útil para colocar objetos en superficies cuando no se requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="7e385-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="7e385-213">Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="7e385-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="7e385-214">Considere la posibilidad de dividir los hologramas extra grandes en partes lógicas y alinear cada parte en la superficie.</span><span class="sxs-lookup"><span data-stu-id="7e385-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="7e385-215">La Interpupillary distancia establecida correctamente (IPD) también puede afectar a la alineación de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7e385-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="7e385-216">Configure siempre HoloLens en el del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-217">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-218">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-218">Documentation</span></span>

* [<span data-ttu-id="7e385-219">Colocación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="7e385-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="7e385-220">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="7e385-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="7e385-221">Procedimientos recomendados para los anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="7e385-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="7e385-222">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="7e385-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="7e385-223">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="7e385-224">Información general sobre el desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="7e385-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-225">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-225">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-226">Kit de herramientas de MR, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="7e385-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="7e385-227">Kit complementario MR, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="7e385-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="7e385-228">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="7e385-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="7e385-229">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="7e385-229">External references</span></span>

* [<span data-ttu-id="7e385-230">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="7e385-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="7e385-231">Ver la zona de confort</span><span class="sxs-lookup"><span data-stu-id="7e385-231">Viewing zone of comfort</span></span>

<span data-ttu-id="7e385-232">Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades.</span><span class="sxs-lookup"><span data-stu-id="7e385-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="7e385-233">Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se fijan a una distancia óptica de aproximadamente 2,0 m del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="7e385-234">Una profundidad de contenido incorrecta puede conducir a la molestia visual o a la fatiga.</span><span class="sxs-lookup"><span data-stu-id="7e385-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-235">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-238">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-239">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="7e385-240">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="7e385-241">Coloque el contenido en 2 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="7e385-242">Cuando los hologramas no se pueden colocar en 2 m y no se pueden evitar los conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="7e385-243">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).</span><span class="sxs-lookup"><span data-stu-id="7e385-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="7e385-244">A menos que el escenario no lo requiera, un plano de recorte debe implementarse con fundido de salida a partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="7e385-245">En los casos en los que se requiere una observación más detallada de un holograma de motionless, el contenido no debe ser más cercano a 50 cm.</span><span class="sxs-lookup"><span data-stu-id="7e385-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="7e385-246">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-246">Meets</span></span></td><td> <span data-ttu-id="7e385-247">El contenido está dentro de la guía de visualización y movimiento, pero se usa inadecuadamente o no se usa el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="7e385-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e385-248">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-248">Fail</span></span> </td><td> <span data-ttu-id="7e385-249">El contenido se presenta demasiado cerca (normalmente &lt; 1,25 m o &lt; 50 cm para los hologramas estacionales que requieren una observación más detallada).</span><span class="sxs-lookup"><span data-stu-id="7e385-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="7e385-250">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-250">How to measure</span></span>

* <span data-ttu-id="7e385-251">Normalmente, el contenido debe ser de 2 m de distancia, pero no más próximo a 1,25 o superior a 5 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="7e385-252">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en 85CM con un fundido de salida de contenido a partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="7e385-253">Acerque el contenido y observe el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="7e385-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="7e385-254">El contenido estacionario no debe estar más cerca de 50 cm de distancia.</span><span class="sxs-lookup"><span data-stu-id="7e385-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-255">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-255">Recommendations</span></span>

* <span data-ttu-id="7e385-256">Diseñe el contenido de la distancia de visualización óptima de 2 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="7e385-257">Establezca la distancia de representación de recorte en 85 cm con atenuación del contenido a partir de 1 m.</span><span class="sxs-lookup"><span data-stu-id="7e385-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="7e385-258">En el caso de los hologramas estacionales que necesitan una visualización más estrecha, el plano de recorte no debe estar más cerca de 30 cm y el fundido de salida debe empezar al menos 10 cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="7e385-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-259">Resources</span></span>

* [<span data-ttu-id="7e385-260">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="7e385-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="7e385-261">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="7e385-262">Experimentación con escala</span><span class="sxs-lookup"><span data-stu-id="7e385-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="7e385-263">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="7e385-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="7e385-264">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="7e385-264">Depth switching</span></span>

<span data-ttu-id="7e385-265">Sin tener en cuenta los problemas de la zona de confort, las demandas del usuario a cambiar con frecuencia o rapidez entre los objetos cercanos y lejanos (incluidos los hologramas y el contenido del mundo real) pueden conducir a la fatiga oculomotor y a la molestia general.</span><span class="sxs-lookup"><span data-stu-id="7e385-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-266">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-269">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-269">✔️</span></span></td>
        <td><span data-ttu-id="7e385-270">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-271">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-271">Quality criteria</span></span>

|  <span data-ttu-id="7e385-272">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-272">Best</span></span>  |  <span data-ttu-id="7e385-273">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-273">Meets</span></span> |  <span data-ttu-id="7e385-274">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-275">Cambio de profundidad limitado o natural que no hace que el usuario se recentre sin ningún problema.</span><span class="sxs-lookup"><span data-stu-id="7e385-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="7e385-276">Cambio de profundidad abrupta: este es el núcleo y está diseñado en la experiencia de la aplicación, o en el modificador de profundidad abrupta causado por contenido real inesperado.</span><span class="sxs-lookup"><span data-stu-id="7e385-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="7e385-277">Conmutador de profundidad coherente o cambio de profundidad brusco que no es necesario ni básico para la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-278">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-278">How to measure</span></span>

* <span data-ttu-id="7e385-279">Si la aplicación requiere que el usuario cambie de forma constante y/o repentinamente el foco de profundidad, hay un problema de conmutación de profundidad.</span><span class="sxs-lookup"><span data-stu-id="7e385-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-280">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-280">Recommendations</span></span>

* <span data-ttu-id="7e385-281">Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="7e385-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="7e385-282">Esto evitará la fatiga oculomotor y el movimiento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="7e385-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-283">Resources</span></span>

* [<span data-ttu-id="7e385-284">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="7e385-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="7e385-285">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="7e385-286">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="7e385-286">Use of spatial sound</span></span>

<span data-ttu-id="7e385-287">En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno.</span><span class="sxs-lookup"><span data-stu-id="7e385-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="7e385-288">El uso de sonido espacial en una aplicación permite a los desarrolladores colocar de forma convincente los sonidos en un espacio tridimensional (esfera) alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="7e385-289">Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="7e385-290">El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="7e385-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-291">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-294">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-294">✔️</span></span></td>
        <td><span data-ttu-id="7e385-295">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-296">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-296">Quality criteria</span></span>

|  <span data-ttu-id="7e385-297">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-297">Best</span></span>  |  <span data-ttu-id="7e385-298">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-298">Meets</span></span> |  <span data-ttu-id="7e385-299">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-300">El sonido está espacial lógicamente y la experiencia de usuario usa correctamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="7e385-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="7e385-301">El sonido es natural y relevante para los objetos y se normaliza en el escenario.</span><span class="sxs-lookup"><span data-stu-id="7e385-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="7e385-302">El audio espacial se utiliza de forma adecuada para aumentar la capacidad de respuesta, pero falta como medio para ayudar con los comentarios de los usuarios y la detectabilidad.</span><span class="sxs-lookup"><span data-stu-id="7e385-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="7e385-303">El sonido no está espacialmente como se esperaba o falta de sonido para ayudar al usuario dentro de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="7e385-304">O el audio espacial no se consideró ni usó en el diseño del escenario.</span><span class="sxs-lookup"><span data-stu-id="7e385-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-305">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-305">How to measure</span></span>

* <span data-ttu-id="7e385-306">En general, los sonidos relevantes deben emitirse desde los hologramas de destino (por ejemplo, el sonido de corteza procedente de holográfica Dog).</span><span class="sxs-lookup"><span data-stu-id="7e385-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="7e385-307">Deben usarse señales sonoras en toda la experiencia del usuario para ayudar al usuario a realizar comentarios o a conocer las acciones que se encuentran fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="7e385-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-308">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-308">Recommendations</span></span>

* <span data-ttu-id="7e385-309">Use el audio espacial para ayudar con la detección de objetos y las interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="7e385-310">Los sonidos reales funcionan mejor que la síntesis o el sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="7e385-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="7e385-311">La mayoría de los sonidos deben ser espaciales.</span><span class="sxs-lookup"><span data-stu-id="7e385-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="7e385-312">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="7e385-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="7e385-313">Evite el enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="7e385-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="7e385-314">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="7e385-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-316">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-316">Documentation</span></span>

* [<span data-ttu-id="7e385-317">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="7e385-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="7e385-318">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="7e385-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="7e385-319">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="7e385-320">Caso práctico, sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="7e385-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="7e385-321">Caso práctico, uso de sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="7e385-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-322">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-322">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-323">Kit de herramientas de realidad mixta (audio espacial)</span><span class="sxs-lookup"><span data-stu-id="7e385-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="7e385-324">Centrarse en los límites de trama holográfica (hipertema)</span><span class="sxs-lookup"><span data-stu-id="7e385-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="7e385-325">Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="7e385-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="7e385-326">Mitigar el efecto de los límites de los hipertextos implica un diseño minucioso de la escala y el contexto del contenido, el uso de audio espacial, los sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="7e385-327">Si se realiza correctamente, el usuario sentirá menos el límite de los límites de los subprocesos, a la vez que tiene una experiencia de aplicación cómoda.</span><span class="sxs-lookup"><span data-stu-id="7e385-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-328">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-331">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-332">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-332">Quality criteria</span></span>

|  <span data-ttu-id="7e385-333">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-333">Best</span></span>  |  <span data-ttu-id="7e385-334">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-334">Meets</span></span> |  <span data-ttu-id="7e385-335">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-336">El usuario nunca pierde el contexto y se siente cómodo.</span><span class="sxs-lookup"><span data-stu-id="7e385-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="7e385-337">Se proporciona asistencia contextual para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="7e385-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="7e385-338">Se proporcionan instrucciones de detección y visualización para los objetos que se encuentran fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="7e385-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="7e385-339">En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="7e385-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="7e385-340">El usuario nunca pierde el contexto, pero es posible que se requiera movimiento de cuello adicional en situaciones limitadas.</span><span class="sxs-lookup"><span data-stu-id="7e385-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="7e385-341">En situaciones limitadas, la escala hace que los hologramas interrumpan el fotograma vertical u horizontal, lo que produce un movimiento de cuello para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7e385-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="7e385-342">Es necesario que el usuario pierda el contexto o el movimiento de cuello coherente para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7e385-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="7e385-343">No hay ninguna guía de contexto para objetos holográficas grandes, el movimiento de objetos es fácil de perder fuera del marco sin ninguna guía de detección, o bien un holograma alto requiere un movimiento de cuello normal para verlo.</span><span class="sxs-lookup"><span data-stu-id="7e385-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-344">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-344">How to measure</span></span>

* <span data-ttu-id="7e385-345">El contexto de un holograma (grande) se pierde o no se entiende debido a que se recortan en los límites.</span><span class="sxs-lookup"><span data-stu-id="7e385-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="7e385-346">Las ubicaciones de los hologramas son difíciles de encontrar debido a la falta de directores de atención o al contenido que mueve y sale rápidamente del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="7e385-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="7e385-347">El escenario requiere un movimiento de cabezal normal y repetitivo hacia arriba y hacia abajo para ver por completo un holograma que dé lugar a una fatiga del cuello.</span><span class="sxs-lookup"><span data-stu-id="7e385-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-348">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-348">Recommendations</span></span>

* <span data-ttu-id="7e385-349">Comience la experiencia con objetos pequeños que se ajusten al objeto de subproceso y, a continuación, transición con indicaciones visuales a versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="7e385-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="7e385-350">Use los directores de audio y atención espaciales para ayudar al usuario a encontrar contenido que está fuera del hipermismo.</span><span class="sxs-lookup"><span data-stu-id="7e385-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="7e385-351">En la medida de lo posible, evite los hologramas que recortan verticalmente el hipernivel.</span><span class="sxs-lookup"><span data-stu-id="7e385-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="7e385-352">Proporcionar al usuario orientación en la aplicación para obtener la mejor ubicación de visualización.</span><span class="sxs-lookup"><span data-stu-id="7e385-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-353">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-354">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-354">Documentation</span></span>

* [<span data-ttu-id="7e385-355">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="7e385-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="7e385-356">Caso práctico, aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="7e385-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="7e385-357">Escala de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="7e385-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="7e385-358">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="7e385-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="7e385-359">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="7e385-359">External references</span></span>

* [<span data-ttu-id="7e385-360">Gran cantidad de ADO sobre el visual</span><span class="sxs-lookup"><span data-stu-id="7e385-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="7e385-361">El contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="7e385-361">Content reacts to user position</span></span>

<span data-ttu-id="7e385-362">Los hologramas deben reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales".</span><span class="sxs-lookup"><span data-stu-id="7e385-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="7e385-363">Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario sea estacional y adaptarse al movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="7e385-364">El diseño de una aplicación que se adapta correctamente a la posición del usuario creará una experiencia más increíble y facilitará su uso.</span><span class="sxs-lookup"><span data-stu-id="7e385-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-365">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-368">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-368">✔️</span></span></td>
        <td><span data-ttu-id="7e385-369">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-370">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="7e385-371">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-371">Best</span></span> </td><td> <span data-ttu-id="7e385-372">El contenido y la interfaz de usuario se adaptan a las posiciones de los usuarios, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito de movimiento esperado</span><span class="sxs-lookup"><span data-stu-id="7e385-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e385-373">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-373">Meets</span></span> </td><td> <span data-ttu-id="7e385-374">La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave que requiere que el usuario ajuste su posición.</span><span class="sxs-lookup"><span data-stu-id="7e385-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7e385-375">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="7e385-376">Los elementos de la interfaz de usuario se pierden o se bloquean durante el movimiento, lo que provoca que el usuario vuelva a los controles (o los busque) de una misma.</span><span class="sxs-lookup"><span data-stu-id="7e385-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="7e385-377">Los elementos de la interfaz de usuario limitan la vista del contenido principal.</span><span class="sxs-lookup"><span data-stu-id="7e385-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="7e385-378">El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el momento, especialmente con elementos de interfaz <a href="../../design/billboarding-and-tag-along.md">de usuario de etiquetas</a> .</span><span class="sxs-lookup"><span data-stu-id="7e385-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="7e385-379">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-379">How to measure</span></span>

* <span data-ttu-id="7e385-380">Todas las medidas deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="7e385-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="7e385-381">Aunque el movimiento del usuario variará, no intente engañar a la aplicación con un movimiento de usuario extremo.</span><span class="sxs-lookup"><span data-stu-id="7e385-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="7e385-382">En el caso de los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="7e385-383">Por ejemplo, si el usuario está viendo y recorriendo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-384">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-384">Recommendations</span></span>

* <span data-ttu-id="7e385-385">El usuario es la cámara y controla el movimiento.</span><span class="sxs-lookup"><span data-stu-id="7e385-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="7e385-386">Dejar que se controlen.</span><span class="sxs-lookup"><span data-stu-id="7e385-386">Let them drive.</span></span>
* <span data-ttu-id="7e385-387">Considere la posibilidad de mostrar los sistemas de texto y de menú que, de otro modo, podrían quedar bloqueados o desconocidos si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="7e385-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="7e385-388">Use la etiqueta junto con el contenido que debe seguir al usuario y, al mismo tiempo, permitir que el usuario vea lo que hay delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="7e385-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-389">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-390">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-390">Documentation</span></span>

* [<span data-ttu-id="7e385-391">Diseño de la interacción</span><span class="sxs-lookup"><span data-stu-id="7e385-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="7e385-392">Color, claro y material</span><span class="sxs-lookup"><span data-stu-id="7e385-392">Color, light, and material</span></span>](../../design/color-light-and-materials.md)
* [<span data-ttu-id="7e385-393">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="7e385-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="7e385-394">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="7e385-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="7e385-395">Automovimiento y locomoción del usuario</span><span class="sxs-lookup"><span data-stu-id="7e385-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="7e385-396">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="7e385-396">Input interaction clarity</span></span>

<span data-ttu-id="7e385-397">La claridad de la interacción de entrada es fundamental para el uso de una aplicación e incluye la coherencia de entrada, la capacidad de enfoque, la detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="7e385-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="7e385-398">El usuario puede usar interacciones comunes en toda la plataforma sin tener que reaprender.</span><span class="sxs-lookup"><span data-stu-id="7e385-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="7e385-399">Si la aplicación tiene una entrada personalizada, debe comunicarse claramente y mostrarse.</span><span class="sxs-lookup"><span data-stu-id="7e385-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-400">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-403">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-403">✔️</span></span></td>
        <td><span data-ttu-id="7e385-404">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-405">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-405">Quality criteria</span></span>

|  <span data-ttu-id="7e385-406">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-406">Best</span></span>  |  <span data-ttu-id="7e385-407">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-407">Meets</span></span> |  <span data-ttu-id="7e385-408">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-409">Los métodos de interacción de entrada son coherentes con las [instrucciones](../../design/interaction-fundamentals.md)proporcionadas por Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7e385-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="7e385-410">Cualquier entrada personalizada no debe ser redundante con entrada estándar (en lugar de usar interacción estándar) y se debe comunicar y mostrar claramente al usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="7e385-411">Similar a lo mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="7e385-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="7e385-412">El usuario puede seguir logrando el objetivo y el progreso a través de la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="7e385-413">Es difícil comprender la asignación de botones o métodos de entrada.</span><span class="sxs-lookup"><span data-stu-id="7e385-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="7e385-414">La entrada está muy personalizada, no admite la entrada estándar, no hay instrucciones o es probable que cause problemas de fatiga y confort.</span><span class="sxs-lookup"><span data-stu-id="7e385-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-415">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-415">How to measure</span></span>

* <span data-ttu-id="7e385-416">La aplicación usa [métodos de entrada estándar](../../design/interaction-fundamentals.md) coherentes.</span><span class="sxs-lookup"><span data-stu-id="7e385-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="7e385-417">Si la aplicación tiene una entrada personalizada, se comunica claramente mediante:</span><span class="sxs-lookup"><span data-stu-id="7e385-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="7e385-418">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="7e385-418">First-run experience</span></span>
* <span data-ttu-id="7e385-419">Pantallas de introducción</span><span class="sxs-lookup"><span data-stu-id="7e385-419">Introductory screens</span></span>
* <span data-ttu-id="7e385-420">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="7e385-420">Tooltips</span></span>
* <span data-ttu-id="7e385-421">Asesor manual</span><span class="sxs-lookup"><span data-stu-id="7e385-421">Hand coach</span></span>
* <span data-ttu-id="7e385-422">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="7e385-422">Help section</span></span>
* <span data-ttu-id="7e385-423">Voice over</span><span class="sxs-lookup"><span data-stu-id="7e385-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-424">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-424">Recommendations</span></span>

* <span data-ttu-id="7e385-425">Utilice los métodos de entrada estándar siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="7e385-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="7e385-426">Proporcione demostraciones, tutoriales e información sobre herramientas para los métodos de entrada no estándar.</span><span class="sxs-lookup"><span data-stu-id="7e385-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="7e385-427">Use un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-428">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-429">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-429">Documentation</span></span>

* [<span data-ttu-id="7e385-430">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="7e385-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="7e385-431">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="7e385-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="7e385-432">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="7e385-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="7e385-433">Cursores</span><span class="sxs-lookup"><span data-stu-id="7e385-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="7e385-434">Confort y mira</span><span class="sxs-lookup"><span data-stu-id="7e385-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="7e385-435">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7e385-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="7e385-436">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="7e385-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="7e385-437">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="7e385-438">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="7e385-439">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="7e385-440">Controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="7e385-441">Gestos en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="7e385-442">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="7e385-443">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="7e385-443">Keyboard, mouse, and controller input in DirectX</span></span>](./keyboard-mouse-and-controller-input-in-directx.md)
* [<span data-ttu-id="7e385-444">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="7e385-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="7e385-445">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="7e385-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="7e385-446">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="7e385-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-447">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-447">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-448">Caso práctico: el logro de más informática personal</span><span class="sxs-lookup"><span data-stu-id="7e385-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="7e385-449">Estudio de conversión: aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="7e385-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="7e385-450">Aplicación de ejemplo: tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="7e385-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="7e385-451">Aplicación de ejemplo: módulo lunar</span><span class="sxs-lookup"><span data-stu-id="7e385-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="7e385-452">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="7e385-452">Interactable objects</span></span>

<span data-ttu-id="7e385-453">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="7e385-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="7e385-454">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="7e385-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="7e385-455">Cualquier elemento puede ser un objeto interactuable que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="7e385-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="7e385-456">Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="7e385-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="7e385-457">Independientemente del formulario, los objetos interactivos deben ser claramente reconocibles por el usuario a través de las indicaciones de audio y visual.</span><span class="sxs-lookup"><span data-stu-id="7e385-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-458">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-461">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-461">✔️</span></span></td>
        <td><span data-ttu-id="7e385-462">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-463">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-463">Quality criteria</span></span>

|  <span data-ttu-id="7e385-464">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-464">Best</span></span>  |  <span data-ttu-id="7e385-465">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-465">Meets</span></span> |  <span data-ttu-id="7e385-466">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-467">Independientemente del formulario, los objetos interactuables se pueden reconocer a través de las indicaciones de audio y visual en tres Estados: inactivo, dirigido y seleccionado.</span><span class="sxs-lookup"><span data-stu-id="7e385-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="7e385-468">"Lo veo, por ejemplo, está claro y se usa de forma coherente en toda la experiencia.</span><span class="sxs-lookup"><span data-stu-id="7e385-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="7e385-469">Los objetos se escalan y distribuyen para permitir la finalización de errores de forma gratuita.</span><span class="sxs-lookup"><span data-stu-id="7e385-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="7e385-470">El usuario puede reconocer objetos como interactivos a través de comentarios de audio o visuales, y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="7e385-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="7e385-471">No se proporcionan indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="7e385-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="7e385-472">Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="7e385-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-473">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-473">How to measure</span></span>

* <span data-ttu-id="7e385-474">Los objetos interactuables son reconocibles como ' interactuable '; incluye botones, menús y contenido específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e385-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="7e385-475">Como regla general, debe haber una indicación visual y de audio cuando el destino es objetos interactivos.</span><span class="sxs-lookup"><span data-stu-id="7e385-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-476">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-476">Recommendations</span></span>

* <span data-ttu-id="7e385-477">Use comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="7e385-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="7e385-478">Los comentarios visuales deben diferenciarse en cada estado de entrada (inactivo, dirigido, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="7e385-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="7e385-479">Los objetos que se pueden interactuar deben escalarse y colocarse para los destinos sin errores.</span><span class="sxs-lookup"><span data-stu-id="7e385-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="7e385-480">Los objetos interactuables agrupados (por ejemplo, una barra de menús o una lista) deben tener el espaciado adecuado para el destino.</span><span class="sxs-lookup"><span data-stu-id="7e385-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="7e385-481">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave Command ("vea esto, dígalo")</span><span class="sxs-lookup"><span data-stu-id="7e385-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-482">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-483">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-483">Documentation</span></span>

* [<span data-ttu-id="7e385-484">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="7e385-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="7e385-485">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="7e385-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="7e385-486">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="7e385-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="7e385-487">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="7e385-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-488">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-488">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-489">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="7e385-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="7e385-490">Detección de salas</span><span class="sxs-lookup"><span data-stu-id="7e385-490">Room scanning</span></span>

<span data-ttu-id="7e385-491">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="7e385-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="7e385-492">La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="7e385-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="7e385-493">Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="7e385-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="7e385-494">Si es necesario que el usuario analice el entorno, debe proporcionar instrucciones claras durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="7e385-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-495">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-498">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-499">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-499">Quality criteria</span></span>

|  <span data-ttu-id="7e385-500">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-500">Best</span></span>  |  <span data-ttu-id="7e385-501">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-501">Meets</span></span> |  <span data-ttu-id="7e385-502">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-503">Visualización de la malla espacial indique a los usuarios que el análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="7e385-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="7e385-504">El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="7e385-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="7e385-505">Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y que no se proporcione información de progreso.</span><span class="sxs-lookup"><span data-stu-id="7e385-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="7e385-506">Ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="7e385-506">No visualization of mesh.</span></span> <span data-ttu-id="7e385-507">No se proporciona información de orientación al usuario sobre dónde buscar, o Cuándo se inicia o se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="7e385-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="7e385-508">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-508">How to measure</span></span>

* <span data-ttu-id="7e385-509">Durante un examen de habitación necesario, se proporcionan instrucciones visuales y de audio que indican dónde buscar y cuándo iniciar y detener el examen.</span><span class="sxs-lookup"><span data-stu-id="7e385-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-510">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-510">Recommendations</span></span>

* <span data-ttu-id="7e385-511">Indique la cantidad del volumen total de los usuarios que debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="7e385-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="7e385-512">Comunicarse cuando el examen se inicia y se detiene, como un indicador de progreso.</span><span class="sxs-lookup"><span data-stu-id="7e385-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="7e385-513">Use una visualización de la malla durante el examen.</span><span class="sxs-lookup"><span data-stu-id="7e385-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="7e385-514">Proporcione guías de audio y visual para animar al usuario a buscar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="7e385-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="7e385-515">Informe al usuario de dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="7e385-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="7e385-516">En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="7e385-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-517">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="7e385-518">Documentación</span><span class="sxs-lookup"><span data-stu-id="7e385-518">Documentation</span></span>

* [<span data-ttu-id="7e385-519">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="7e385-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="7e385-520">Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e385-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="7e385-521">Caso práctico: diseño de sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="7e385-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="7e385-522">Caso práctico: creación de una experiencia envolvente en fragmentos</span><span class="sxs-lookup"><span data-stu-id="7e385-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="7e385-523">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="7e385-523">Tools and tutorials</span></span>

* [<span data-ttu-id="7e385-524">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="7e385-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="7e385-525">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="7e385-525">Directional indicators</span></span>

<span data-ttu-id="7e385-526">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista o ocluidos por objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="7e385-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="7e385-527">Una aplicación bien diseñada facilitará a los usuarios la búsqueda de contenido no visible.</span><span class="sxs-lookup"><span data-stu-id="7e385-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="7e385-528">Los indicadores direccionales avisan a un usuario de contenido importante y proporcionan orientación sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="7e385-529">Las instrucciones para el contenido no visible pueden adoptar la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="7e385-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-530">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-533">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-533">✔️</span></span></td>
        <td><span data-ttu-id="7e385-534">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-535">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-535">Quality criteria</span></span>

|  <span data-ttu-id="7e385-536">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-536">Best</span></span>  |  <span data-ttu-id="7e385-537">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-537">Meets</span></span> |  <span data-ttu-id="7e385-538">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-539">Las guías de audio y visual guían directamente al usuario al contenido relevante fuera del campo de vista.</span><span class="sxs-lookup"><span data-stu-id="7e385-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="7e385-540">Una flecha o algún indicador que apunta al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="7e385-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="7e385-541">El contenido relevante está fuera del campo de vista y no se proporciona ninguna guía de ubicación para el usuario.</span><span class="sxs-lookup"><span data-stu-id="7e385-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="7e385-542">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-542">How to measure</span></span>

* <span data-ttu-id="7e385-543">El contenido relevante fuera del campo de vista de usuario se detecta mediante señales de audio o visual.</span><span class="sxs-lookup"><span data-stu-id="7e385-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-544">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-544">Recommendations</span></span>

* <span data-ttu-id="7e385-545">Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="7e385-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="7e385-546">En muchos casos, se prefiere una guía visual directa a las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="7e385-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="7e385-547">Los indicadores direccionales no se deben integrar en el cursor.</span><span class="sxs-lookup"><span data-stu-id="7e385-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-548">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-548">Resources</span></span>

* [<span data-ttu-id="7e385-549">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="7e385-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="7e385-550">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="7e385-550">Data loading</span></span>

<span data-ttu-id="7e385-551">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="7e385-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="7e385-552">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo puede ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="7e385-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="7e385-553">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7e385-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e385-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7e385-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e385-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e385-556">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-556">✔️</span></span></td>
        <td><span data-ttu-id="7e385-557">✔️</span><span class="sxs-lookup"><span data-stu-id="7e385-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="7e385-558">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="7e385-558">Quality criteria</span></span>

|  <span data-ttu-id="7e385-559">Óptima</span><span class="sxs-lookup"><span data-stu-id="7e385-559">Best</span></span>  |  <span data-ttu-id="7e385-560">Reúne</span><span class="sxs-lookup"><span data-stu-id="7e385-560">Meets</span></span> |  <span data-ttu-id="7e385-561">Suspenso</span><span class="sxs-lookup"><span data-stu-id="7e385-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="7e385-562">Indicador visual animado, en forma de una barra de progreso o un anillo, que muestra el progreso durante cualquier carga o procesamiento de datos.</span><span class="sxs-lookup"><span data-stu-id="7e385-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="7e385-563">El indicador visual proporciona instrucciones sobre cuánto tiempo puede ser la espera.</span><span class="sxs-lookup"><span data-stu-id="7e385-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="7e385-564">Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="7e385-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="7e385-565">No hay ningún indicador de carga de datos o de proceso para que la tarea tarde más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="7e385-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="7e385-566">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="7e385-566">How to measure</span></span>

* <span data-ttu-id="7e385-567">Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="7e385-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="7e385-568">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="7e385-568">Recommendations</span></span>

* <span data-ttu-id="7e385-569">Proporcionar un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se haya detenido o bloqueado.</span><span class="sxs-lookup"><span data-stu-id="7e385-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="7e385-570">Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="7e385-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="7e385-571">Recursos</span><span class="sxs-lookup"><span data-stu-id="7e385-571">Resources</span></span>

* [<span data-ttu-id="7e385-572">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="7e385-572">Displaying progress</span></span>](../../design/progress.md)