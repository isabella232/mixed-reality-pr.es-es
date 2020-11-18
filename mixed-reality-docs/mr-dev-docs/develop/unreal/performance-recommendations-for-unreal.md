---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549133"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="886f1-104">Recomendaciones de rendimiento para Unreal</span><span class="sxs-lookup"><span data-stu-id="886f1-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="886f1-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="886f1-105">Overview</span></span>

<span data-ttu-id="886f1-106">Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), pero se centra en las características específicas de Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="886f1-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="886f1-107">Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="886f1-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="886f1-108">Configuración del proyecto de Unreal recomendada</span><span class="sxs-lookup"><span data-stu-id="886f1-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="886f1-109">Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="886f1-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="886f1-110">Uso el representador de VR móvil:</span><span class="sxs-lookup"><span data-stu-id="886f1-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="886f1-111">Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).</span><span class="sxs-lookup"><span data-stu-id="886f1-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="886f1-113">Uso de la opción Forward Renderer (Representador progresivo):</span><span class="sxs-lookup"><span data-stu-id="886f1-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="886f1-114">Esta característica es mucho mejor para la realidad mixta que la canalización de representación diferida predeterminada.</span><span class="sxs-lookup"><span data-stu-id="886f1-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="886f1-115">Esto se debe principalmente al número de características que pueden desactivarse individualmente.</span><span class="sxs-lookup"><span data-stu-id="886f1-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="886f1-116">Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="886f1-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Representación progresiva](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="886f1-118">Uso del modo multivista móvil:</span><span class="sxs-lookup"><span data-stu-id="886f1-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="886f1-119">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil).</span><span class="sxs-lookup"><span data-stu-id="886f1-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="886f1-120">La opción Mobile HDR (Alto rango dinámico móvil) debe estar desactivada.</span><span class="sxs-lookup"><span data-stu-id="886f1-120">Mobile HDR should be unchecked.</span></span>

![Configuración de representación de VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="886f1-122">Asegúrese de que **Predeterminado** o **D3D12** son los valores de **RHI predeterminado** al usar OpenXR.</span><span class="sxs-lookup"><span data-stu-id="886f1-122">Ensure **Default** or **D3D12** is the selected **Default RHI** when using OpenXR.</span></span>
    * <span data-ttu-id="886f1-123">Si selecciona **D3D11** tendrá un efecto negativo en el rendimiento debido a que la plataforma tiene que realizar una fase de representación adicional.</span><span class="sxs-lookup"><span data-stu-id="886f1-123">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="886f1-124">Puede que **D3D12** proporcione mejoras en el rendimiento de la representación, además de evitar la fase de representación adicional.</span><span class="sxs-lookup"><span data-stu-id="886f1-124">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI predeterminado](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="886f1-126">Deshabilitación de la niebla de los vértices:</span><span class="sxs-lookup"><span data-stu-id="886f1-126">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="886f1-127">Con la niebla de los vértices se aplican cálculos de niebla en cada vértice de un polígono y, a continuación, se interpolan los resultados a lo largo del polígono.</span><span class="sxs-lookup"><span data-stu-id="886f1-127">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="886f1-128">Si el juego no usa niebla, debe elegir esta opción para deshabilitar la niebla con el fin de aumentar el rendimiento del sombreado.</span><span class="sxs-lookup"><span data-stu-id="886f1-128">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Opciones de la niebla de los vértices](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="886f1-130">Deshabilitación de la selección de la oclusión:</span><span class="sxs-lookup"><span data-stu-id="886f1-130">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="886f1-131">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).</span><span class="sxs-lookup"><span data-stu-id="886f1-131">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="886f1-132">Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación).</span><span class="sxs-lookup"><span data-stu-id="886f1-132">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="886f1-133">Esto permite que Unreal realice el trabajo en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="886f1-133">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="886f1-134">La selección de la oclusión en la GPU en dispositivos móviles es un proceso lento.</span><span class="sxs-lookup"><span data-stu-id="886f1-134">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="886f1-135">Por lo general, le recomendamos que la GPU esté principalmente relacionada con la representación.</span><span class="sxs-lookup"><span data-stu-id="886f1-135">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="886f1-136">Si cree que la oclusión permitirá mejorar el rendimiento, intente habilitar la oclusión de software en su lugar.</span><span class="sxs-lookup"><span data-stu-id="886f1-136">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="886f1-137">Tenga en cuenta que la habilitación de la oclusión de software podría empeorar el rendimiento si ya está limitado por la CPU debido a un gran número de llamadas de dibujo.</span><span class="sxs-lookup"><span data-stu-id="886f1-137">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Deshabilitación de la selección de la oclusión](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="886f1-139">Deshabilitación de la fase de la galería de símbolos de profundidad personalizada:</span><span class="sxs-lookup"><span data-stu-id="886f1-139">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="886f1-140">Esta característica requiere un paso adicional, lo que significa que su procesamiento es lento.</span><span class="sxs-lookup"><span data-stu-id="886f1-140">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="886f1-141">La translucidez también es un proceso lento en Unreal.</span><span class="sxs-lookup"><span data-stu-id="886f1-141">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="886f1-142">Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="886f1-142">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Galería de símbolos de profundidad](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="886f1-144">Reducción de mapas de sombras en cascada:</span><span class="sxs-lookup"><span data-stu-id="886f1-144">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="886f1-145">La reducción del número de mapas de sombras mejorará el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="886f1-145">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="886f1-146">Por lo general, debe establecerse en 1 a menos que haya una pérdida de calidad visible.</span><span class="sxs-lookup"><span data-stu-id="886f1-146">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Mapas de instantáneas en cascada](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="886f1-148">Configuración opcional</span><span class="sxs-lookup"><span data-stu-id="886f1-148">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="886f1-149">La configuración siguiente puede mejorar el rendimiento, pero a costa de deshabilitar determinadas características.</span><span class="sxs-lookup"><span data-stu-id="886f1-149">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="886f1-150">Use esta configuración solo si está seguro de que no necesita las características en cuestión.</span><span class="sxs-lookup"><span data-stu-id="886f1-150">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="886f1-151">Reducción de permutación del sombreador móvil</span><span class="sxs-lookup"><span data-stu-id="886f1-151">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="886f1-152">Si las luces no se mueven independientemente de la cámara, puede establecer este valor en 0 sin problemas.</span><span class="sxs-lookup"><span data-stu-id="886f1-152">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="886f1-153">La principal ventaja es que permitirá que Unreal seleccione varias permutaciones del sombreador, lo que acelera la compilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="886f1-153">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Reducción de permutación del sombreador móvil](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="886f1-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="886f1-155">See also</span></span>
* [<span data-ttu-id="886f1-156">Instrucciones de rendimiento móvil de Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="886f1-156">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)