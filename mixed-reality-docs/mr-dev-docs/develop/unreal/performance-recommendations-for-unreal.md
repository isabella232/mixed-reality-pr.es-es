---
title: Recomendaciones de rendimiento para Unreal
description: Obtenga información sobre cómo lograr el mejor rendimiento de las aplicaciones de realidad mixta con la configuración de proyecto de Unreal recomendada.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583067"
---
# <a name="performance-recommendations-for-unreal"></a>Recomendaciones de rendimiento para Unreal

Unreal Engine tiene varias características que pueden aumentar el rendimiento de las aplicaciones, todas basadas en la explicación que se describe en [recomendaciones de rendimiento para la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.

## <a name="recommended-unreal-project-settings"></a>Configuración del proyecto de Unreal recomendada

Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).

1. Uso el representador de VR móvil:
    * Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. Uso de la opción Forward Renderer (Representador progresivo): 
    * El representador progresivo es mucho mejor para la realidad mixta que la canalización de representación diferida predeterminada debido al número de características que pueden desactivarse individualmente. 
    * Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).

![Representación progresiva](images/unreal/performance-recommendations-img-04.png)

3. Uso del modo multivista móvil:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil). La opción Mobile HDR (Alto rango dinámico móvil) debe estar desactivada.

![Configuración de representación de VR](images/unreal/performance-recommendations-img-03.png)

4. **[Solo para OpenXR]** Asegúrese de que **Predeterminado** o **D3D12** son los valores de **RHI predeterminado**:
    * Si selecciona **D3D11** tendrá un efecto negativo en el rendimiento debido a que la plataforma tiene que realizar una fase de representación adicional. Puede que **D3D12** proporcione mejoras en el rendimiento de la representación, además de evitar la fase de representación adicional.

![RHI predeterminado](images/unreal/performance-recommendations-img-09.png)

5. Deshabilitación de la niebla de los vértices: 
    * Con la niebla de los vértices se aplican cálculos de niebla en cada vértice de un polígono y, a continuación, se interpolan los resultados a lo largo del polígono. Si el juego no usa niebla, se recomienda deshabilitar la niebla de los vértices para aumentar el rendimiento del sombreado.

![Opciones de la niebla de los vértices](images/unreal/performance-recommendations-img-05.png)

6. Deshabilitación de la selección de la oclusión:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).
        + Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación). Unreal realizará el trabajo en la CPU y evitará las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.
    * La selección de la oclusión en la GPU en dispositivos móviles es un proceso lento. Por lo general, le recomendamos que la GPU esté principalmente relacionada con la representación. Si cree que la oclusión permitirá mejorar el rendimiento, intente habilitar la oclusión de software en su lugar. 

> [!NOTE]
> La habilitación de la oclusión de software podría empeorar el rendimiento si ya está limitado por la CPU debido a un gran número de llamadas de dibujo.

![Deshabilitación de la selección de la oclusión](images/unreal/performance-recommendations-img-02.png)

7. Deshabilitación de la fase de la galería de símbolos de profundidad personalizada:
    * La deshabilitación de la galería de símbolos de profundidad personalizada requiere un paso adicional, lo que significa que es lenta. La translucidez también es un proceso lento en Unreal. Puede encontrar más información en la [documentación de Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).

![Galería de símbolos de profundidad](images/unreal/performance-recommendations-img-06.png)

8. Reducción de mapas de sombras en cascada: 
    * La reducción del número de mapas de sombras mejorará el rendimiento. Por lo general, debe establecer la propiedad en 1, a menos que haya una pérdida de calidad visible. 

![Mapas de instantáneas en cascada](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>Configuración opcional

> [!NOTE]
> La configuración siguiente puede mejorar el rendimiento, pero a costa de deshabilitar determinadas características. Use esta configuración solo si está seguro de que no necesita las características en cuestión.

1. Reducción de permutación del sombreador móvil
    * Si las luces no se mueven independientemente de la cámara, puede establecer este valor de la propiedad en 0 sin problemas. La principal ventaja es que permitirá que Unreal seleccione varias permutaciones del sombreador, lo que acelera la compilación del sombreador.

![Reducción de permutación del sombreador móvil](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>Consulte también

* [Instrucciones de rendimiento móvil de Unreal Engine]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)