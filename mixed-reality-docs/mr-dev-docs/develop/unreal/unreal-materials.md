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
# <a name="material-recommendations-in-unreal"></a>Recomendaciones de material en no real

Los materiales pueden hacer o interrumpir el rendimiento en un motor inreal. Esta página actúa como una guía de inicio rápido de la configuración básica que debe usar para obtener el mejor rendimiento.

## <a name="using-customizeduvs"></a>Usar CustomizedUVs

Si necesita proporcionar un mosaico de UVs en el material, debe usar CustomizedUVs en lugar de modificar el UV del nodo de textura directamente. CustomizedUVs permiten la manipulación de UV en los sombreadores de vértices en lugar de sombreador de píxeles. 

![Configuración de materiales en no real](images/unreal-materials-img-01c.png)

Puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) y los ejemplos de procedimientos recomendados en las siguientes capturas de pantallas:

[ ![ Configuración de material recomendada en configuración ](images/unreal-materials-img-01.png) de ](images/unreal-materials-img-01.png#lightbox)material no real 
 *recomendada*

[ ![ Configuración de material no recomendada en ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)la configuración de 
 *material no recomendado no* real

## <a name="changing-blend-mode"></a>Cambiar el modo de mezcla

Debe establecer el modo de mezcla en opaco a menos que haya una razón importante para hacer lo contrario. Los materiales enmascarados y translúcidos son lentos. Puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Cambiar el modo de mezcla](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Actualización de la iluminación para dispositivos móviles

La precisión completa debe estar desactivada. La iluminación lightmap se puede marcar mediante la activación de información direccional. Cuando está deshabilitada, la iluminación de lightmaps será plana pero más barata.

![Configuración de material móvil en no real](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Ajustar el sombreado hacia delante

Estas opciones mejoran la fidelidad visual a costa del rendimiento. Deben estar desactivadas para obtener el máximo rendimiento.

![Desplazar valores de configuración de material en no real](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Configuración del material translucidez

Indica que el material translúcido no debe verse afectado por el floración o DOF. Dado que ambos efectos son poco frecuentes en MR, este valor debe estar activado de forma predeterminada.

![Configuración de translucidez independiente para móviles en no real](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Configuración opcional

La configuración siguiente puede mejorar el rendimiento, pero tenga en cuenta que deshabilitan determinadas características. Use estas opciones solo si está seguro de que no necesita las características en cuestión.

![Configuración de materiales opcional en no real](images/unreal-materials-img-06.jpg)

Si el material no requiere reflejos ni brillo, el establecimiento de esta opción puede proporcionar una mejora enorme del rendimiento. En las pruebas internas, es tan rápido como "sin iluminación" y proporciona información de iluminación.

## <a name="best-practices"></a>Procedimientos recomendados

Los siguientes elementos no son "Settings", ya que son procedimientos recomendados relacionados con materiales.

Al crear parámetros, es preferible usar "parámetros estáticos" siempre que sea posible. Los modificadores estáticos se pueden usar para quitar una rama completa de un material sin costo en tiempo de ejecución. Las instancias pueden tener valores diferentes, lo que permite tener una configuración de sombreador con plantilla sin pérdida de rendimiento. Sin embargo, el inconveniente es que crea muchas permutaciones que producirán una gran cantidad de recompilación del sombreador. Intente minimizar el número de parámetros estáticos en el material y el número de permutaciones de los parámetros estáticos que se usan realmente. Puede encontrar más información sobre la representación de parámetros de material en la [documentación del motor inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Prácticas recomendadas para la configuración de materiales](images/unreal-materials-img-07.jpg)

Al crear instancias de materiales, se debe aplicar la preferencia a la **constante de instancia de material** en la instancia de material dinámica. La **constante de instancia de material** es un material con instancias que calcula solo una vez, antes del tiempo de ejecución.

La instancia de material creada mediante el explorador de contenido ( **haga clic con el botón derecho en > crear instancia de material** ) es una constante de instancia de material. La instancia de material dinámica se crea mediante código. Puede encontrar más detalles sobre las instancias de material en la [documentación del motor inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Crear instancias de material en no real](images/unreal-materials-img-08.png)

Vigile la complejidad de los materiales y los sombreadores. Para ver el costo del material en varias plataformas, haga clic en el icono estadísticas de la plataforma. También puede encontrar más detalles sobre los materiales en la [documentación del motor inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Crear configuraciones dinámicas de instancias de materiales en el mismo](images/unreal-materials-img-09.png)

Puede obtener una idea rápida de la complejidad relativa de su sombreador a través del [modo de vista](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)complejidad del sombreador.

* Hotkey del modo de vista: Alt + 8
* Comando de consola: ViewMode shadercomplexity

![Complejidad del material en el inreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Consulte también
* [Materiales móviles](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modos de vista](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Instancias de materiales](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
