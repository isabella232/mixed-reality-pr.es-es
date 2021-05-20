---
title: Visualización de la exploración de la sala
description: Las aplicaciones que requieren asignación espacial usan el dispositivo para recopilar datos a lo largo del tiempo y entre sesiones.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicación, diseño, HoloLens, examen de sala, asignación espacial, malla, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196410"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="92e0b-104">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="92e0b-104">Room scan visualization</span></span>

<span data-ttu-id="92e0b-105">Las aplicaciones que requieren asignación espacial dependen del dispositivo para recopilar datos a lo largo del tiempo y entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="92e0b-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="92e0b-106">La integridad y calidad de los datos de asignación depende de muchos factores, incluida la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos, como los alimentos y las puertas, se han movido desde que el dispositivo ha examinado el área.</span><span class="sxs-lookup"><span data-stu-id="92e0b-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="92e0b-107">Para garantizar datos útiles de asignación espacial, los desarrolladores de aplicaciones tienen varias opciones:</span><span class="sxs-lookup"><span data-stu-id="92e0b-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="92e0b-108">Dependa de lo que ya se haya recopilado.</span><span class="sxs-lookup"><span data-stu-id="92e0b-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="92e0b-109">Estos datos pueden estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="92e0b-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="92e0b-110">Pida al usuario que use el gesto de Bloom para llegar al Windows Mixed Reality inicio y, a continuación, explore el área que desea usar para la experiencia.</span><span class="sxs-lookup"><span data-stu-id="92e0b-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="92e0b-111">Pueden usar la pulsación en el aire para confirmar que el dispositivo conoce toda la área necesaria.</span><span class="sxs-lookup"><span data-stu-id="92e0b-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="92e0b-112">Cree una experiencia de exploración personalizada en su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="92e0b-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="92e0b-113">En todos estos casos, el sistema almacena los datos reales recopilados durante la exploración y la aplicación no necesita hacerlo.</span><span class="sxs-lookup"><span data-stu-id="92e0b-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="92e0b-114">Si quiere ver la visualización del examen de sala en acción, consulte nuestra demostración de vídeo Diseño de **hologramas:** reconocimiento espacial a continuación:</span><span class="sxs-lookup"><span data-stu-id="92e0b-114">If you'd like to see room scan visualization in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="92e0b-115">*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="92e0b-115">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="device-support"></a><span data-ttu-id="92e0b-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="92e0b-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92e0b-117"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="92e0b-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="92e0b-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="92e0b-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="92e0b-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="92e0b-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92e0b-120">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="92e0b-120">Room scan visualization</span></span></td>
        <td><span data-ttu-id="92e0b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="92e0b-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="92e0b-122">Creación de una experiencia de análisis personalizada</span><span class="sxs-lookup"><span data-stu-id="92e0b-122">Building a custom scanning experience</span></span>

<span data-ttu-id="92e0b-123">Las aplicaciones pueden analizar los datos de asignación espacial al principio de la experiencia para determinar si quieren que el usuario realice pasos adicionales para mejorar su integridad y calidad.</span><span class="sxs-lookup"><span data-stu-id="92e0b-123">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="92e0b-124">Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización que se superponga en el mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="92e0b-124">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="92e0b-125">¿Cuánto del volumen total en las proximidades de los usuarios debe formar parte de la experiencia?</span><span class="sxs-lookup"><span data-stu-id="92e0b-125">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="92e0b-126">Dónde debe ir el usuario para mejorar los datos</span><span class="sxs-lookup"><span data-stu-id="92e0b-126">Where the user should go to improve data</span></span>

<span data-ttu-id="92e0b-127">Los usuarios no saben qué hace que un examen sea "bueno".</span><span class="sxs-lookup"><span data-stu-id="92e0b-127">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="92e0b-128">Se les debe mostrar o saber qué buscar si se les pide que evalúen un examen: plana, distancia desde las paredes reales, entre otros.</span><span class="sxs-lookup"><span data-stu-id="92e0b-128">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="92e0b-129">El desarrollador debe implementar un bucle de comentarios que incluya la actualización de los datos de asignación espacial durante la fase de exploración o exploración.</span><span class="sxs-lookup"><span data-stu-id="92e0b-129">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="92e0b-130">En muchos casos, es mejor decir al usuario lo que necesita hacer para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="92e0b-130">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="92e0b-131">Por ejemplo, mire el tope, mire detrás de los suelos, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="92e0b-131">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="92e0b-132">Caché frente a asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="92e0b-132">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="92e0b-133">Los datos de asignación espacial son las aplicaciones de origen de datos de mayor peso que pueden consumir.</span><span class="sxs-lookup"><span data-stu-id="92e0b-133">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="92e0b-134">Para evitar problemas de rendimiento, como fotogramas descartados o desordenes, el consumo de estos datos debe realizarse cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="92e0b-134">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="92e0b-135">El examen activo durante una experiencia puede ser beneficioso y perjudicial, por lo que deberá decidir qué método usar en función de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="92e0b-135">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="92e0b-136">Asignación espacial almacenada en caché</span><span class="sxs-lookup"><span data-stu-id="92e0b-136">Cached spatial mapping</span></span>

<span data-ttu-id="92e0b-137">Si hay datos de asignación espacial almacenados en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y usa esta instantánea durante la experiencia.</span><span class="sxs-lookup"><span data-stu-id="92e0b-137">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="92e0b-138">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="92e0b-138">**Benefits**</span></span>
* <span data-ttu-id="92e0b-139">Se ha reducido la sobrecarga en el sistema mientras se ejecuta la experiencia, lo que provoca importantes mejoras en el rendimiento de la energía, las temperaturas y la CPU.</span><span class="sxs-lookup"><span data-stu-id="92e0b-139">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="92e0b-140">Una implementación más sencilla de la experiencia principal, ya que los cambios en los datos espaciales no la interrumpen.</span><span class="sxs-lookup"><span data-stu-id="92e0b-140">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="92e0b-141">Un solo costo de un solo tiempo en cualquier procesamiento posterior de los datos espaciales para fines físicos, gráficos y otros fines.</span><span class="sxs-lookup"><span data-stu-id="92e0b-141">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="92e0b-142">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="92e0b-142">**Drawbacks**</span></span>
* <span data-ttu-id="92e0b-143">Los datos almacenados en caché no reflejan el movimiento de objetos o personas del mundo real.</span><span class="sxs-lookup"><span data-stu-id="92e0b-143">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="92e0b-144">Por ejemplo, la aplicación podría considerar una puerta abierta cuando está cerrada ahora.</span><span class="sxs-lookup"><span data-stu-id="92e0b-144">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="92e0b-145">Potencialmente más memoria de aplicación para mantener la versión almacenada en caché de los datos.</span><span class="sxs-lookup"><span data-stu-id="92e0b-145">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="92e0b-146">Un buen caso para este método es un entorno controlado o un juego de mesa.</span><span class="sxs-lookup"><span data-stu-id="92e0b-146">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="92e0b-147">Asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="92e0b-147">Continuous spatial mapping</span></span>

<span data-ttu-id="92e0b-148">Algunas aplicaciones pueden basarse en el análisis continuo para actualizar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="92e0b-148">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="92e0b-149">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="92e0b-149">**Benefits**</span></span>
* <span data-ttu-id="92e0b-150">No es necesario compilar en una experiencia de exploración o exploración independiente por adelantado en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="92e0b-150">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="92e0b-151">El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con algún retraso.</span><span class="sxs-lookup"><span data-stu-id="92e0b-151">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="92e0b-152">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="92e0b-152">**Drawbacks**</span></span>
* <span data-ttu-id="92e0b-153">Mayor complejidad en la implementación de la experiencia principal.</span><span class="sxs-lookup"><span data-stu-id="92e0b-153">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="92e0b-154">Posible sobrecarga del procesamiento físico y gráfico adicional, ya que estos sistemas deben ingerir los cambios de forma incremental.</span><span class="sxs-lookup"><span data-stu-id="92e0b-154">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="92e0b-155">Mayor impacto en la energía, la temperatura y la CPU.</span><span class="sxs-lookup"><span data-stu-id="92e0b-155">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="92e0b-156">Un buen caso para este método es aquel en el que se espera que los hologramas interactúen con objetos en movimiento, por ejemplo, un automóvil holográfico que conduce por el suelo puede querer entrar en una puerta en función de si está abierto o cerrado.</span><span class="sxs-lookup"><span data-stu-id="92e0b-156">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="92e0b-157">Consulta también</span><span class="sxs-lookup"><span data-stu-id="92e0b-157">See also</span></span>

* [<span data-ttu-id="92e0b-158">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="92e0b-158">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="92e0b-159">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="92e0b-159">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="92e0b-160">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="92e0b-160">Spatial sound design</span></span>](spatial-sound-design.md)