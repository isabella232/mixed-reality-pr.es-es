---
title: Recomendaciones de material en Unreal
description: Información general sobre los materiales del motor de Unreal.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, development, materials, documentation, guides, features, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: d5ce702495c95e8ca6d07a0209a4bc7d02f5d4d682415b028d63995e8910a7e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187740"
---
# <a name="material-recommendations-in-unreal"></a>Recomendaciones de material en Unreal

Los materiales que use pueden afectar directamente a la ejecución de los proyectos en Unreal Engine. Esta página actúa como un inicio rápido para la configuración básica que debe usar para obtener el mejor rendimiento de las aplicaciones de realidad mixta.

## <a name="using-customizeduvs"></a>Uso deUVs personalizados

Si necesita proporcionar un tiling UV en el material, use CustomUVs en lugar de modificar directamente la UV del nodo de textura. Los UVS personalizados permiten manipular los UV en los sombreadores de vértices en lugar del sombreador de píxeles.

![Configuración de material en Unreal](images/unreal-materials-img-01c.png)

Puede encontrar detalles de material en la documentación [de Unreal Engine y](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) ejemplos de procedimientos recomendados en las capturas de pantalla siguientes:

[ ![ Configuración de material ](images/unreal-materials-img-01.png) recomendada en La configuración de ](images/unreal-materials-img-01.png#lightbox) 
 *material recomendada de* Unreal

[ ![ Configuración de material no ](images/unreal-materials-img-01b.png) recomendada en la configuración de ](images/unreal-materials-img-01b.png#lightbox) 
 *material no recomendado de* Unreal

## <a name="changing-blend-mode"></a>Cambiar el modo blend

Se recomienda establecer el modo de mezcla en opaco a menos que haya un motivo seguro para hacer lo contrario. Los materiales enmascarados y translúcidos son lentos. Puede encontrar más detalles sobre los materiales en la [documentación de Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Cambio del modo de mezcla](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Actualización de la iluminación para dispositivos móviles

Se debe desactivar la precisión completa. La iluminación de mapa de luz se puede marcar hacia abajo desactivando la información direccional. Cuando se deshabilita, la iluminación de los mapas de luz será plana, pero más económica.

![Configuración de material móvil en Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Ajustar el sombreado hacia delante

Estas opciones mejoran la fidelidad visual a costa del rendimiento. Deben desactivarse para obtener el máximo rendimiento.

![Configuración de material de sombreado hacia delante en Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Establecimiento de la translucencia de material

Indica que el material translúcido no debe verse afectado por bloom o DOF. Dado que ambos efectos son poco frecuentes en MR, esta configuración debe estar en on de forma predeterminada.

![Configuración de translucencia independiente para dispositivos móviles en Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Configuración opcional

La siguiente configuración puede mejorar el rendimiento, pero tenga en cuenta que deshabilita determinadas características. Use esta configuración solo si está seguro de que no necesita las características en cuestión.

![Configuración de material opcional en Unreal](images/unreal-materials-img-06.jpg)

Si el material no requiere reflexión ni brillo, establecer esta opción puede proporcionar un gran aumento del rendimiento. En las pruebas internas, es tan rápido como "sin iluminación" mientras se proporciona información de iluminación.

## <a name="best-practices"></a>Procedimientos recomendados

Los siguientes no son "configuración" tanto como procedimientos recomendados relacionados con los materiales.

Al crear parámetros, se prefiere usar "Parámetros estáticos" siempre que sea posible. Los modificadores estáticos se pueden usar para quitar una rama completa de un material sin costo en tiempo de ejecución. Las instancias pueden tener valores diferentes, lo que permite configurar un sombreador con plantilla sin pérdida de rendimiento. La desventaja es que se crean varias permutaciones que provocarán la recompilación del sombreador. Intente minimizar el número de parámetros estáticos en el material y el número de permutaciones de los parámetros estáticos que se usan. Puede encontrar más detalles sobre la representación de parámetros de material en la [documentación de Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Procedimientos recomendados para la configuración de materiales](images/unreal-materials-img-07.jpg)

Al crear instancias de material, se debe dar preferencia a constante de instancia **de material sobre** dinámica de instancia de material. **Constante de instancia de** material es un material de instancia que calcula solo una vez antes del tiempo de ejecución.

La instancia de material creada a través de Content Browser (haga clic con el botón derecho > Crear instancia de **material)** es una constante de instancia de material. Material Instance Dynamic se crea mediante código. Puede encontrar más detalles sobre las instancias de material en la [documentación de Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Creación de instancias de material en Unreal](images/unreal-materials-img-08.png)

Tenga en cuenta la complejidad de los materiales o sombreadores. Para ver el costo del material en varias plataformas, haga clic en el icono Estadísticas de plataforma. También puede encontrar más detalles sobre los materiales en la [documentación de Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Creación de una configuración dinámica de instancia de material en Unreal](images/unreal-materials-img-09.png)

Puede obtener una idea rápida de la complejidad relativa del sombreador a través del modo de vista complejidad [del sombreador](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).

* Tecla de acceso rápido del modo de vista: Alt + 8
* Comando de consola: viewmode shadercomplexity

![Complejidad material en Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Vea también
* [Materiales móviles](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Modos de vista](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Instancias de material](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
