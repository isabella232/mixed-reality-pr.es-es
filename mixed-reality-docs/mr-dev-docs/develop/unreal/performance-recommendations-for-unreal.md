---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699287"
---
# <a name="performance-recommendations-for-unreal"></a>Recomendaciones de rendimiento para Unreal

## <a name="overview"></a>Introducción

Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), pero se centra en las características específicas de Unreal Engine. Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.

## <a name="recommended-unreal-project-settings"></a>Configuración del proyecto de Unreal recomendada
Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).

1. Uso el representador de VR móvil:
    * Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. Uso de la opción Forward Renderer (Representador progresivo): 
    * Esta característica es mucho mejor para la realidad mixta que la canalización de representación diferida predeterminada. Esto se debe principalmente al número de características que pueden desactivarse individualmente. 
    * Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Representación progresiva](images/unreal/performance-recommendations-img-04.png)

3. Deshabilitación de la niebla de los vértices: 
    * Con la niebla de los vértices se aplican cálculos de niebla en cada vértice de un polígono y, a continuación, se interpolan los resultados a lo largo del polígono. Si el juego no usa niebla, debe elegir esta opción para deshabilitar la niebla con el fin de aumentar el rendimiento del sombreado.

![Opciones de la niebla de los vértices](images/unreal/performance-recommendations-img-05.png)

4. Deshabilitación de la selección de la oclusión:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).
        + Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación). Esto permite que Unreal realice el trabajo en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.
    * La selección de la oclusión en la GPU en dispositivos móviles es un proceso lento. Por lo general, le recomendamos que la GPU esté principalmente relacionada con la representación. Si cree que la oclusión permitirá mejorar el rendimiento, intente habilitar la oclusión de software en su lugar. Tenga en cuenta que la habilitación de la oclusión de software podría empeorar el rendimiento si ya está limitado por la CPU debido a un gran número de llamadas de dibujo.

![Deshabilitación de la selección de la oclusión](images/unreal/performance-recommendations-img-02.png)

    
5. Deshabilitación de la galería de símbolos de profundidad:
    * Esta característica requiere un paso adicional, lo que significa que su procesamiento es lento. La translucidez también es un proceso lento en Unreal. Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Galería de símbolos de profundidad](images/unreal/performance-recommendations-img-06.png)

6. Uso del modo multivista móvil:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil). La opción Mobile HDR (Alto rango dinámico móvil) debe estar desactivada.

![Configuración de representación de VR](images/unreal/performance-recommendations-img-03.png)

7. Reducción de mapas de sombras en cascada: 
    * La reducción del número de mapas de sombras mejorará el rendimiento. Por lo general, debe establecerse en 1 a menos que haya una pérdida de calidad visible. 

![Mapas de instantáneas en cascada](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Configuración opcional

> [!NOTE]
> La configuración siguiente puede mejorar el rendimiento, pero a costa de deshabilitar determinadas características. Use esta configuración solo si está seguro de que no necesita las características en cuestión.

1. Reducción de permutación del sombreador móvil
    * Si las luces no se mueven independientemente de la cámara, puede establecer este valor en 0 sin problemas. La principal ventaja es que permitirá que Unreal seleccione varias permutaciones del sombreador, lo que acelera la compilación del sombreador.

![Reducción de permutación del sombreador móvil](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Consulte también
* [Instrucciones de rendimiento móvil de Unreal Engine]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)