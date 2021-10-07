---
title: Aspectos básicos de la calidad
description: Obtenga información sobre los aspectos básicos de calidad del diseño de aplicaciones de realidad mixta.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: aspectos básicos de calidad, caso práctico, proyecto, ejemplo, MRTK, Mixed Reality Toolkit, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647538"
---
# <a name="quality-fundamentals"></a>Aspectos básicos de la calidad

Quality Fundamentals es una HoloLens 2 que muestra los aspectos básicos de la creación de una experiencia de realidad mixta excelente.  En lugar de simplemente aprender y leer sobre los problemas de calidad en la realidad mixta, ahora podemos experimentar problemas comunes de entorno, diseño y rendimiento y soluciones de primera mano mediante la selección de las opciones proporcionadas en la aplicación.

Para descargar e instalar la aplicación, vaya a la página de descarga de la aplicación:

> [!div class="nextstepaction"]
> [Aspectos básicos de la calidad](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Página principal de aspectos básicos de calidad](images\qf-homepage.jpg)

En esta aplicación de ejemplo, veremos lo siguiente:

>[!div class = "checklist"]
> * [Entorno y E/S del](#device-io-and-environment)dispositivo: cómo los factores del entorno pueden afectar al HoloLens" del dispositivo.
> * [Spatial Anchors:](#anchor-fundamentals)cómo alinear hologramas con un espacio físico mediante delimitadores espaciales.
> * [Estabilidad holográfica y fidelidad:](#stability-and-fidelity)explore técnicas para ayudar a mejorar la estabilidad y la fidelidad de Hologramas.
> * [Aspectos básicos de los recursos 3D:](#3d-asset-fundamentals)cómo optimizar los recursos 3D para mantener una alta fidelidad visual. 

## <a name="device-io-and-environment"></a>Entorno y E/S del dispositivo

Inicie la aplicación Fundamentos de calidad en HoloLens. Una vez que aparezca la página principal de la aplicación, seleccione **E/S de dispositivo y Entorno.**  Exploraremos cómo los sensores de HoloLens y el entorno circundante afectan a la asignación espacial, el seguimiento y la colocación de hologramas. 

### <a name="surfaces"></a>Superficies

Los reflejos o superficies con acabados reflejados pueden confundir los HoloLens sensores sobre la forma del objeto.  El dispositivo puede interpretar los objetos reflejados en la superficie como entorno cambiante, lo que puede hacer que el dispositivo pierda el seguimiento.  Si las superficies reflejadas están causando desafíos para los HoloLens, considere la posibilidad de agregar una pantalla o unas cesáus.

Para obtener más información, [vea las superficies de un espacio](/hololens/hololens-environment-considerations#surfaces-in-a-space) en HoloLens [consideraciones sobre el entorno](/hololens/hololens-environment-considerations).

### <a name="lighting"></a>Iluminación

HoloLens rendimiento se puede ver afectado negativamente por condiciones de luz muy bajas o muy brillantes.  Los sensores de seguimiento de HoloLens necesitan alrededor de 500-1000 bombillas para funcionar de forma óptima. Puede usar un medidor o una aplicación móvil para medir la cantidad de luz en el espacio.

Para obtener más información, vea [iluminación](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) en [HoloLens consideraciones sobre el entorno](/hololens/hololens-environment-considerations).

## <a name="anchor-fundamentals"></a>Aspectos básicos del anclaje

Para explorar cómo usar Spatial Anchors alinear los hologramas con un espacio físico, seleccione **DelimitadorEstos en** la página principal de la aplicación.

En esta parte de la aplicación, exploraremos los siguientes escenarios de usuario:

>[!div class = "checklist"]
> * ¿Qué ocurre cuando no se aplica ningún delimitador a un objeto ?
> * Cuando se Spatial Anchors varios objetos para un grupo de objetos .
> * Uso compartido de un delimitador espacial entre varios colaboradores mediante un código QR.
> * Colocación de delimitadores para objetos muy grandes en un espacio.

Para obtener más información, [vea Spatial Anchors](../../design/spatial-anchors.md) en la [documentación Mixed Reality](../../design/spatial-anchors.md) datos.

## <a name="stability-and-fidelity"></a>Estabilidad y fidelidad

En la página principal de la aplicación, seleccione **Estabilidad y fidelidad para** explorar cómo mejorar la estabilidad del holograma.

Exploraremos los siguientes conceptos clave:

>[!div class = "checklist"]
> * [Velocidad de fotogramas.](#frame-rate)
> * [Reproducción en fase tardía (LSR).](#late-stage-reprojection-lsr)
> * [Z-fighting](#z-fighting).
> * [Suavizado de alias.](#anti-aliasing)

### <a name="frame-rate"></a>Velocidad de fotogramas

Para proporcionar la mejor experiencia de holograma posible, los desarrolladores de aplicaciones deben mantener 60 fotogramas por segundo (FPS).  En esta parte de la aplicación, alterne entre diferentes opciones de recuento de triángulos para experimentar la diferencia con varias velocidades de fotogramas.

![Optimización del recuento de triángulos](images\qf-triangle-count-optimization.png)

Para obtener más información, consulte [velocidad de fotogramas](../platform-capabilities-and-apis/hologram-stability.md#frame-rate) en el [artículo estabilidad del holograma.](../platform-capabilities-and-apis/hologram-stability.md)

### <a name="late-stage-reprojection-lsr"></a>Reproducción en fase tardía (LSR)

La reproducción se usa para estabilizar los hologramas a medida que los usuarios se mueven alrededor de su espacio.  Pruebe las distintas opciones de reproducción proporcionadas por esta parte de la aplicación para ver la diferencia en la calidad del holograma.

![Pruebe las distintas opciones de reproducción para experimentar la diferencia.](images\qf-lsr-modes.jpg)

Para obtener información detallada, consulte [reproducción en](../platform-capabilities-and-apis/hologram-stability.md#reprojection) el artículo [estabilidad del holograma.](../platform-capabilities-and-apis/hologram-stability.md)

### <a name="z-fighting"></a>Z-fighting

La Z-fighting se produce cuando la aplicación de realidad mixta no puede distinguir qué objeto está delante del otro.  Observará el parpadeo de los objetos holográficos mientras buscan el mismo valor de profundidad Z.  Experimente los efectos de Z-fighting en la aplicación cambiando la colocación de un objeto holográfico, el logotipo en una bicicleta en este caso.

![Experimente z-fighting con colocaciones de objetos.](images\qf-z-fighting.jpg)

Para obtener información detallada sobre z-fighting, consulte habilitación del uso compartido de [búferes de](./recommended-settings-for-unity.md#enable-depth-buffer-sharing) profundidad en [el artículo configuración recomendada para Unity.](./recommended-settings-for-unity.md)

### <a name="anti-aliasing"></a>Suavizado de alias

El suavizado de contorno es una técnica que se usa para suavizar los bordes irregulares en líneas curvas y diagonales en hologramas.  En esta parte de la aplicación, experimente los efectos del alias en los radios de texto y bicicleta mostrados.  

## <a name="3d-asset-fundamentals"></a>Aspectos básicos de los recursos 3D

En la página principal de la aplicación, seleccione **3D Asset Fundamentals (Aspectos** básicos de los recursos 3D) para explorar cómo optimizar los recursos 3D para cumplir el requisito de velocidad de fotogramas y mantener la alta fidelidad visual.

Exploraremos los siguientes conceptos clave:

>[!div class = "checklist"]
> * [Recuento de triángulos.](#triangle-count)
> * [El sombreador pasa](#shader-passes).
> * [Draw llama a](#draw-calls).
> * [Finalizar .](#finale)

### <a name="triangle-count"></a>Recuento de triángulos

Seleccione el número y la complejidad de los modelos de bicicletas para experimentar la diferencia visual en función de FPS.

![Elija diferentes opciones de recuento de triángulos para ver los efectos en la velocidad de fotogramas.](images\qf-3d-asset-visible-triangles.jpg)

Para más información, consulte proceso [de creación de recursos.](../../design/asset-creation-process.md)

### <a name="shader-passes"></a>Pases de sombreador

Seleccione el número de bicicletas y las distintas opciones de sombreador para experimentar la diferencia visual en función de FPS.

![Elija distintas opciones de sombreador para ver los efectos en la velocidad de fotogramas.](images\qf-3d-asset-shader-complexity.jpg)

Para obtener más información, vea [MrTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Draw calls (Dibujar llamadas)

Las llamadas a draw son llamadas que consumen muchos recursos a la tarjeta gráfica.  En esta parte de la aplicación, experimente la diferencia visual de primera mano, ya que el número de llamadas a draw afecta a FPS.

![Las llamadas a Draw deben optimizarse para aumentar el rendimiento.](images\qf-3d-asset-draw-calls.jpg)

Consulte [Recomendaciones de rendimiento de CPU a GPU.](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Final

Aquí, podemos explorar cuántas bicicletas totalmente optimizadas se pueden mostrar y el nivel de fidelidad posible dadas las técnicas de optimización.

![Técnicas de optimización utilizadas.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Pasos siguientes

Explore otros escenarios de ejemplo de realidad mixta:

   > [!div class="nextstepaction"]
   > [Aplicaciones de ejemplo y características](../features-and-samples.md)