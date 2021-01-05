---
title: Visualización de la exploración de la sala
description: Las aplicaciones que requieren asignación espacial usan el dispositivo para recopilar datos a lo largo del tiempo y entre sesiones.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, exploración de salón, asignación espacial, malla, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens
ms.openlocfilehash: f4ec072c8fde8d3e7e390bd837116a8262bac38b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848247"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="443b0-104">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="443b0-104">Room scan visualization</span></span>

<span data-ttu-id="443b0-105">Las aplicaciones que requieren asignación espacial dependen del dispositivo para recopilar datos a lo largo del tiempo y entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="443b0-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="443b0-106">La integridad y la calidad de los datos de asignación dependen de muchos factores, incluida la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="443b0-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="443b0-107">Para garantizar datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:</span><span class="sxs-lookup"><span data-stu-id="443b0-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="443b0-108">Confíe en lo que ya se ha recopilado.</span><span class="sxs-lookup"><span data-stu-id="443b0-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="443b0-109">Estos datos pueden estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="443b0-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="443b0-110">Pida al usuario que use el gesto de floración para llegar a la Página principal de Windows Mixed Reality y, a continuación, explore el área que desean usar para la experiencia.</span><span class="sxs-lookup"><span data-stu-id="443b0-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="443b0-111">Pueden utilizar la pulsación aérea para confirmar que el dispositivo conoce todo el área necesaria.</span><span class="sxs-lookup"><span data-stu-id="443b0-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="443b0-112">Cree una experiencia de exploración personalizada en su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="443b0-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="443b0-113">En todos estos casos, el sistema almacena los datos reales recopilados durante la exploración y la aplicación no necesita hacerlo.</span><span class="sxs-lookup"><span data-stu-id="443b0-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="443b0-114">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="443b0-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="443b0-115"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="443b0-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="443b0-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="443b0-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="443b0-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="443b0-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="443b0-118">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="443b0-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="443b0-119">✔️</span><span class="sxs-lookup"><span data-stu-id="443b0-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="443b0-120">Generar una experiencia de exploración personalizada</span><span class="sxs-lookup"><span data-stu-id="443b0-120">Building a custom scanning experience</span></span>

<span data-ttu-id="443b0-121">Las aplicaciones pueden analizar los datos de asignación espacial al principio de la experiencia para juzgar si desean que el usuario realice pasos adicionales para mejorar su integridad y calidad.</span><span class="sxs-lookup"><span data-stu-id="443b0-121">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="443b0-122">Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización de superposición en todo el mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="443b0-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="443b0-123">La cantidad del volumen total de los usuarios en proximidad debe formar parte de la experiencia</span><span class="sxs-lookup"><span data-stu-id="443b0-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="443b0-124">Dónde debe ir el usuario para mejorar los datos</span><span class="sxs-lookup"><span data-stu-id="443b0-124">Where the user should go to improve data</span></span>

<span data-ttu-id="443b0-125">Los usuarios no saben lo que realiza un análisis "correcto".</span><span class="sxs-lookup"><span data-stu-id="443b0-125">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="443b0-126">Es necesario que se muestren o se les indique lo que debe buscar si se les pide que evalúen un examen: la curvatura, la distancia de las paredes reales, etc.</span><span class="sxs-lookup"><span data-stu-id="443b0-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="443b0-127">El desarrollador debe implementar un bucle de comentarios que incluya la actualización de los datos de asignación espacial durante la fase de exploración o exploración.</span><span class="sxs-lookup"><span data-stu-id="443b0-127">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="443b0-128">En muchos casos, es mejor indicar al usuario lo que necesita hacer para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="443b0-128">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="443b0-129">Por ejemplo, mire el límite superior, mire detrás del mobiliario, etc.</span><span class="sxs-lookup"><span data-stu-id="443b0-129">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="443b0-130">Asignación espacial en caché y continua</span><span class="sxs-lookup"><span data-stu-id="443b0-130">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="443b0-131">Los datos de asignación espacial son el peso más pesado que pueden consumir las aplicaciones de origen de datos.</span><span class="sxs-lookup"><span data-stu-id="443b0-131">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="443b0-132">Para evitar problemas de rendimiento, como fotogramas quitados o intermitencias, el consumo de estos datos debe realizarse con cuidado.</span><span class="sxs-lookup"><span data-stu-id="443b0-132">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="443b0-133">El análisis activo durante una experiencia puede ser beneficioso y perjudicial, por lo que deberá decidir qué método usar en función de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="443b0-133">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="443b0-134">Asignación espacial almacenada en caché</span><span class="sxs-lookup"><span data-stu-id="443b0-134">Cached spatial mapping</span></span>

<span data-ttu-id="443b0-135">Si hay datos de asignación espacial en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y usa esta instantánea durante la experiencia.</span><span class="sxs-lookup"><span data-stu-id="443b0-135">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="443b0-136">**Beneficios**</span><span class="sxs-lookup"><span data-stu-id="443b0-136">**Benefits**</span></span>
* <span data-ttu-id="443b0-137">Reducción de la sobrecarga en el sistema mientras se ejecuta la experiencia, lo que supone una mejora considerable en el rendimiento de la CPU, la temperatura y el consumo de energía.</span><span class="sxs-lookup"><span data-stu-id="443b0-137">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="443b0-138">Una implementación más sencilla de la experiencia principal, ya que no se ve interrumpida por los cambios en los datos espaciales.</span><span class="sxs-lookup"><span data-stu-id="443b0-138">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="443b0-139">Un único costo de tiempo en cualquier procesamiento posterior de los datos espaciales para la física, los gráficos y otros propósitos.</span><span class="sxs-lookup"><span data-stu-id="443b0-139">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="443b0-140">**Desventajas**</span><span class="sxs-lookup"><span data-stu-id="443b0-140">**Drawbacks**</span></span>
* <span data-ttu-id="443b0-141">El movimiento de objetos o personas reales no se refleja en los datos almacenados en caché.</span><span class="sxs-lookup"><span data-stu-id="443b0-141">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="443b0-142">por ejemplo, la aplicación puede considerar una puerta abierta cuando se cierra ahora.</span><span class="sxs-lookup"><span data-stu-id="443b0-142">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="443b0-143">Posiblemente más memoria de la aplicación para mantener la versión en caché de los datos.</span><span class="sxs-lookup"><span data-stu-id="443b0-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="443b0-144">Un buen caso para este método es un entorno controlado o una tabla principal del juego.</span><span class="sxs-lookup"><span data-stu-id="443b0-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="443b0-145">Asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="443b0-145">Continuous spatial mapping</span></span>

<span data-ttu-id="443b0-146">Algunas aplicaciones pueden basarse en el análisis continuo para actualizar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="443b0-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="443b0-147">**Beneficios**</span><span class="sxs-lookup"><span data-stu-id="443b0-147">**Benefits**</span></span>
* <span data-ttu-id="443b0-148">No es necesario compilar en una experiencia de exploración o exploración independiente de antemano en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="443b0-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="443b0-149">El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con algún retraso.</span><span class="sxs-lookup"><span data-stu-id="443b0-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="443b0-150">**Desventajas**</span><span class="sxs-lookup"><span data-stu-id="443b0-150">**Drawbacks**</span></span>
* <span data-ttu-id="443b0-151">Mayor complejidad en la implementación de la experiencia principal.</span><span class="sxs-lookup"><span data-stu-id="443b0-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="443b0-152">Sobrecarga potencial del procesamiento físico y gráfico adicional, ya que estos sistemas deben ingerir los cambios de forma incremental.</span><span class="sxs-lookup"><span data-stu-id="443b0-152">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="443b0-153">Mayor potencia, térmico y impacto de la CPU.</span><span class="sxs-lookup"><span data-stu-id="443b0-153">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="443b0-154">Un buen caso para este método es aquél en el que se espera que los hologramas interactúen con los objetos de movimiento, por ejemplo, un coche holográfica que las unidades del piso quieran golpear en una puerta, en función de si están abiertos o cerrados.</span><span class="sxs-lookup"><span data-stu-id="443b0-154">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="443b0-155">Consulta también</span><span class="sxs-lookup"><span data-stu-id="443b0-155">See also</span></span>

* [<span data-ttu-id="443b0-156">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="443b0-156">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="443b0-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="443b0-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="443b0-158">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="443b0-158">Spatial sound design</span></span>](spatial-sound-design.md)
