---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: a369a68f8ebf9b7084c22f0efa3bbf0bf5ecbebf
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865430"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="f74fd-104">Recomendaciones de rendimiento para Unreal</span><span class="sxs-lookup"><span data-stu-id="f74fd-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="f74fd-105">Unreal Engine tiene varias características que pueden aumentar el rendimiento de las aplicaciones, todas basadas en la explicación que se describe en [recomendaciones de rendimiento para la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="f74fd-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="f74fd-106">Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f74fd-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="f74fd-107">Configuración del proyecto de Unreal recomendada</span><span class="sxs-lookup"><span data-stu-id="f74fd-107">Recommended Unreal project settings</span></span>
<span data-ttu-id="f74fd-108">Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="f74fd-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="f74fd-109">Uso el representador de VR móvil:</span><span class="sxs-lookup"><span data-stu-id="f74fd-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="f74fd-110">Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).</span><span class="sxs-lookup"><span data-stu-id="f74fd-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="f74fd-112">Uso de la opción Forward Renderer (Representador progresivo):</span><span class="sxs-lookup"><span data-stu-id="f74fd-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="f74fd-113">El representador progresivo es mucho mejor para la realidad mixta que la canalización de representación diferida predeterminada debido al número de características que pueden desactivarse individualmente.</span><span class="sxs-lookup"><span data-stu-id="f74fd-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="f74fd-114">Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="f74fd-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Representación progresiva](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="f74fd-116">Uso del modo multivista móvil:</span><span class="sxs-lookup"><span data-stu-id="f74fd-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="f74fd-117">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil).</span><span class="sxs-lookup"><span data-stu-id="f74fd-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="f74fd-118">La opción Mobile HDR (Alto rango dinámico móvil) debe estar desactivada.</span><span class="sxs-lookup"><span data-stu-id="f74fd-118">Mobile HDR should be unchecked.</span></span>

![Configuración de representación de VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="f74fd-120">**[Solo para OpenXR]** Asegúrese de que **Predeterminado** o **D3D12** son los valores de **RHI predeterminado**:</span><span class="sxs-lookup"><span data-stu-id="f74fd-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="f74fd-121">Si selecciona **D3D11** tendrá un efecto negativo en el rendimiento debido a que la plataforma tiene que realizar una fase de representación adicional.</span><span class="sxs-lookup"><span data-stu-id="f74fd-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="f74fd-122">Puede que **D3D12** proporcione mejoras en el rendimiento de la representación, además de evitar la fase de representación adicional.</span><span class="sxs-lookup"><span data-stu-id="f74fd-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI predeterminado](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="f74fd-124">Deshabilitación de la niebla de los vértices:</span><span class="sxs-lookup"><span data-stu-id="f74fd-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="f74fd-125">Con la niebla de los vértices se aplican cálculos de niebla en cada vértice de un polígono y, a continuación, se interpolan los resultados a lo largo del polígono.</span><span class="sxs-lookup"><span data-stu-id="f74fd-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="f74fd-126">Si el juego no usa niebla, se recomienda deshabilitar la niebla de los vértices para aumentar el rendimiento del sombreado.</span><span class="sxs-lookup"><span data-stu-id="f74fd-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Opciones de la niebla de los vértices](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="f74fd-128">Deshabilitación de la selección de la oclusión:</span><span class="sxs-lookup"><span data-stu-id="f74fd-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="f74fd-129">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).</span><span class="sxs-lookup"><span data-stu-id="f74fd-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="f74fd-130">Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación).</span><span class="sxs-lookup"><span data-stu-id="f74fd-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="f74fd-131">Unreal realizará el trabajo en la CPU y evitará las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f74fd-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="f74fd-132">La selección de la oclusión en la GPU en dispositivos móviles es un proceso lento.</span><span class="sxs-lookup"><span data-stu-id="f74fd-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="f74fd-133">Por lo general, le recomendamos que la GPU esté principalmente relacionada con la representación.</span><span class="sxs-lookup"><span data-stu-id="f74fd-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="f74fd-134">Si cree que la oclusión permitirá mejorar el rendimiento, intente habilitar la oclusión de software en su lugar.</span><span class="sxs-lookup"><span data-stu-id="f74fd-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="f74fd-135">La habilitación de la oclusión de software podría empeorar el rendimiento si ya está limitado por la CPU debido a un gran número de llamadas de dibujo.</span><span class="sxs-lookup"><span data-stu-id="f74fd-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Deshabilitación de la selección de la oclusión](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="f74fd-137">Deshabilitación de la fase de la galería de símbolos de profundidad personalizada:</span><span class="sxs-lookup"><span data-stu-id="f74fd-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="f74fd-138">La deshabilitación de la galería de símbolos de profundidad personalizada requiere un paso adicional, lo que significa que es lenta.</span><span class="sxs-lookup"><span data-stu-id="f74fd-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="f74fd-139">La translucidez también es un proceso lento en Unreal.</span><span class="sxs-lookup"><span data-stu-id="f74fd-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="f74fd-140">Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="f74fd-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Galería de símbolos de profundidad](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="f74fd-142">Reducción de mapas de sombras en cascada:</span><span class="sxs-lookup"><span data-stu-id="f74fd-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="f74fd-143">La reducción del número de mapas de sombras mejorará el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f74fd-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="f74fd-144">Por lo general, debe establecer la propiedad en 1, a menos que haya una pérdida de calidad visible.</span><span class="sxs-lookup"><span data-stu-id="f74fd-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Mapas de instantáneas en cascada](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="f74fd-146">Configuración opcional</span><span class="sxs-lookup"><span data-stu-id="f74fd-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="f74fd-147">La configuración siguiente puede mejorar el rendimiento, pero a costa de deshabilitar determinadas características.</span><span class="sxs-lookup"><span data-stu-id="f74fd-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="f74fd-148">Use esta configuración solo si está seguro de que no necesita las características en cuestión.</span><span class="sxs-lookup"><span data-stu-id="f74fd-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="f74fd-149">Reducción de permutación del sombreador móvil</span><span class="sxs-lookup"><span data-stu-id="f74fd-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="f74fd-150">Si las luces no se mueven independientemente de la cámara, puede establecer este valor de la propiedad en 0 sin problemas.</span><span class="sxs-lookup"><span data-stu-id="f74fd-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="f74fd-151">La principal ventaja es que permitirá que Unreal seleccione varias permutaciones del sombreador, lo que acelera la compilación del sombreador.</span><span class="sxs-lookup"><span data-stu-id="f74fd-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Reducción de permutación del sombreador móvil](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="f74fd-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f74fd-153">See also</span></span>
* [<span data-ttu-id="f74fd-154">Instrucciones de rendimiento móvil de Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="f74fd-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)