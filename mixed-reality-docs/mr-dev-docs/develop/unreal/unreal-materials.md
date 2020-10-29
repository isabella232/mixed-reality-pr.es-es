---
title: Recomendaciones de material en no real
description: Información general de los materiales en el motor inreal.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: No real, en el motor 4, UE4, HoloLens, HoloLens 2, desarrollo, materiales, documentación, guías, características, hologramas, desarrollo de juegos
ms.openlocfilehash: bfce6e6bf8acd58821dba1213e1f1ab571d85a0c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691834"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="395a6-104">Recomendaciones de material en no real</span><span class="sxs-lookup"><span data-stu-id="395a6-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="395a6-105">Los materiales pueden hacer o interrumpir el rendimiento en un motor inreal.</span><span class="sxs-lookup"><span data-stu-id="395a6-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="395a6-106">Esta página actúa como una guía de inicio rápido de la configuración básica que debe usar para obtener el mejor rendimiento.</span><span class="sxs-lookup"><span data-stu-id="395a6-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="395a6-107">Usar CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="395a6-107">Using CustomizedUVs</span></span>

<span data-ttu-id="395a6-108">Si necesita proporcionar un mosaico de UVs en el material, debe usar CustomizedUVs en lugar de modificar el UV del nodo de textura directamente.</span><span class="sxs-lookup"><span data-stu-id="395a6-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="395a6-109">CustomizedUVs permiten la manipulación de UV en los sombreadores de vértices en lugar de sombreador de píxeles.</span><span class="sxs-lookup"><span data-stu-id="395a6-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Configuración de materiales en no real](images/unreal-materials-img-01c.png)

<span data-ttu-id="395a6-111">Puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) y los ejemplos de procedimientos recomendados en las siguientes capturas de pantallas:</span><span class="sxs-lookup"><span data-stu-id="395a6-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="395a6-112">[ ![ Configuración de material recomendada en configuración ](images/unreal-materials-img-01.png) de ](images/unreal-materials-img-01.png#lightbox)material no real 
 *recomendada*</span><span class="sxs-lookup"><span data-stu-id="395a6-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="395a6-113">[ ![ Configuración de material no recomendada en ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)la configuración de 
 *material no recomendado no* real</span><span class="sxs-lookup"><span data-stu-id="395a6-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="395a6-114">Cambiar el modo de mezcla</span><span class="sxs-lookup"><span data-stu-id="395a6-114">Changing Blend Mode</span></span>

<span data-ttu-id="395a6-115">Debe establecer el modo de mezcla en opaco a menos que haya una razón importante para hacer lo contrario.</span><span class="sxs-lookup"><span data-stu-id="395a6-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="395a6-116">Los materiales enmascarados y translúcidos son lentos.</span><span class="sxs-lookup"><span data-stu-id="395a6-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="395a6-117">Puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="395a6-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Cambiar el modo de mezcla](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="395a6-119">Actualización de la iluminación para dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="395a6-119">Updating lighting for mobile</span></span>

<span data-ttu-id="395a6-120">La precisión completa debe estar desactivada.</span><span class="sxs-lookup"><span data-stu-id="395a6-120">Full precision should be turned off.</span></span> <span data-ttu-id="395a6-121">La iluminación lightmap se puede marcar mediante la activación de información direccional.</span><span class="sxs-lookup"><span data-stu-id="395a6-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="395a6-122">Cuando está deshabilitada, la iluminación de lightmaps será plana pero más barata.</span><span class="sxs-lookup"><span data-stu-id="395a6-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Configuración de material móvil en no real](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="395a6-124">Ajustar el sombreado hacia delante</span><span class="sxs-lookup"><span data-stu-id="395a6-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="395a6-125">Estas opciones mejoran la fidelidad visual a costa del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="395a6-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="395a6-126">Deben estar desactivadas para obtener el máximo rendimiento.</span><span class="sxs-lookup"><span data-stu-id="395a6-126">They should be turned off for maximum performance.</span></span>

![Desplazar valores de configuración de material en no real](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="395a6-128">Configuración del material translucidez</span><span class="sxs-lookup"><span data-stu-id="395a6-128">Setting material translucency</span></span>

<span data-ttu-id="395a6-129">Indica que el material translúcido no debe verse afectado por el floración o DOF.</span><span class="sxs-lookup"><span data-stu-id="395a6-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="395a6-130">Dado que ambos efectos son poco frecuentes en MR, este valor debe estar activado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="395a6-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Configuración de translucidez independiente para móviles en no real](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="395a6-132">Configuración opcional</span><span class="sxs-lookup"><span data-stu-id="395a6-132">Optional settings</span></span>

<span data-ttu-id="395a6-133">La configuración siguiente puede mejorar el rendimiento, pero tenga en cuenta que deshabilitan determinadas características.</span><span class="sxs-lookup"><span data-stu-id="395a6-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="395a6-134">Use estas opciones solo si está seguro de que no necesita las características en cuestión.</span><span class="sxs-lookup"><span data-stu-id="395a6-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Configuración de materiales opcional en no real](images/unreal-materials-img-06.jpg)

<span data-ttu-id="395a6-136">Si el material no requiere reflejos ni brillo, el establecimiento de esta opción puede proporcionar una mejora enorme del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="395a6-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="395a6-137">En las pruebas internas, es tan rápido como "sin iluminación" y proporciona información de iluminación.</span><span class="sxs-lookup"><span data-stu-id="395a6-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="395a6-138">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="395a6-138">Best practices</span></span>

<span data-ttu-id="395a6-139">Los siguientes elementos no son "Settings", ya que son procedimientos recomendados relacionados con materiales.</span><span class="sxs-lookup"><span data-stu-id="395a6-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="395a6-140">Al crear parámetros, es preferible usar "parámetros estáticos" siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="395a6-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="395a6-141">Los modificadores estáticos se pueden usar para quitar una rama completa de un material sin costo en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="395a6-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="395a6-142">Las instancias pueden tener valores diferentes, lo que permite tener una configuración de sombreador con plantilla sin pérdida de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="395a6-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="395a6-143">Sin embargo, el inconveniente es que crea muchas permutaciones que producirán una gran cantidad de recompilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="395a6-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="395a6-144">Intente minimizar el número de parámetros estáticos en el material y el número de permutaciones de los parámetros estáticos que se usan realmente.</span><span class="sxs-lookup"><span data-stu-id="395a6-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="395a6-145">Puede encontrar más información sobre la representación de parámetros de material en la [documentación del motor inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="395a6-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Prácticas recomendadas para la configuración de materiales](images/unreal-materials-img-07.jpg)

<span data-ttu-id="395a6-147">Al crear instancias de materiales, se debe aplicar la preferencia a la **constante de instancia de material** en la instancia de material dinámica.</span><span class="sxs-lookup"><span data-stu-id="395a6-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="395a6-148">La **constante de instancia de material** es un material con instancias que calcula solo una vez, antes del tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="395a6-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="395a6-149">La instancia de material creada mediante el explorador de contenido ( **haga clic con el botón derecho en > crear instancia de material** ) es una constante de instancia de material.</span><span class="sxs-lookup"><span data-stu-id="395a6-149">The material instance created via the Content Browser ( **right-click > Create Material Instance** ) is a Material Instance Constant.</span></span> <span data-ttu-id="395a6-150">La instancia de material dinámica se crea mediante código.</span><span class="sxs-lookup"><span data-stu-id="395a6-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="395a6-151">Puede encontrar más detalles sobre las instancias de material en la [documentación del motor inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="395a6-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Crear instancias de material en no real](images/unreal-materials-img-08.png)

<span data-ttu-id="395a6-153">Vigile la complejidad de los materiales y los sombreadores.</span><span class="sxs-lookup"><span data-stu-id="395a6-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="395a6-154">Para ver el costo del material en varias plataformas, haga clic en el icono estadísticas de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="395a6-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="395a6-155">También puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="395a6-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Crear configuraciones dinámicas de instancias de materiales en el mismo](images/unreal-materials-img-09.png)

<span data-ttu-id="395a6-157">Puede obtener una idea rápida de la complejidad relativa de su sombreador a través del [modo de vista](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)complejidad del sombreador.</span><span class="sxs-lookup"><span data-stu-id="395a6-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="395a6-158">Hotkey del modo de vista: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="395a6-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="395a6-159">Comando de consola: ViewMode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="395a6-159">Console command: viewmode shadercomplexity</span></span>

![Complejidad del material en el inreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="395a6-161">Consulte también</span><span class="sxs-lookup"><span data-stu-id="395a6-161">See also</span></span>
* [<span data-ttu-id="395a6-162">Materiales móviles</span><span class="sxs-lookup"><span data-stu-id="395a6-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="395a6-163">Modos de vista</span><span class="sxs-lookup"><span data-stu-id="395a6-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="395a6-164">Instancias de materiales</span><span class="sxs-lookup"><span data-stu-id="395a6-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
