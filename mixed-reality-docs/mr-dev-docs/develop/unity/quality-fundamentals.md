---
title: Aspectos básicos de la calidad
description: Obtenga información sobre los aspectos básicos de calidad del diseño de aplicaciones de realidad mixta.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: aspectos básicos de calidad, caso práctico, proyecto, ejemplo, MRTK, Mixed Reality Toolkit, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: e91ea1c69aeafaafa9c9bae30af6e5a288754764
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702952"
---
# <a name="quality-fundamentals"></a>Aspectos básicos de la calidad

Aspectos básicos de calidad es HoloLens 2 aplicación que muestra los aspectos básicos de la creación de una excelente experiencia de realidad mixta.  En lugar de simplemente aprender y leer sobre los problemas de calidad en la realidad mixta, ahora podemos experimentar problemas comunes de entorno, diseño y rendimiento y soluciones de primera mano seleccionando las opciones proporcionadas en la aplicación.

Para descargar e instalar la aplicación, vaya a la página de descarga de la aplicación:

> [!div class="nextstepaction"]
> [Aspectos básicos de la calidad](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Página principal de aspectos básicos de calidad](images\qf-homepage.jpg)

En esta aplicación de ejemplo, veremos lo siguiente:

>[!div class = "checklist"]
> * [Entorno y E/S del](#device-io-and-environment)dispositivo: cómo los factores ambientales pueden afectar al HoloLens" del dispositivo.
> * [Spatial Anchors:](#anchor-fundamentals)Cómo alinear hologramas con un espacio físico mediante delimitadores espaciales.
> * [Estabilidad holográfica y fidelidad:](#stability-and-fidelity)explore técnicas para ayudar a mejorar la estabilidad y la fidelidad de Hologramas.
> * [Aspectos básicos de los recursos 3D:](#3d-asset-fundamentals)cómo optimizar los recursos 3D para mantener una alta fidelidad visual. 

## <a name="device-io-and-environment"></a>Entorno y E/S de dispositivo

Inicie la aplicación Quality Fundamentals en HoloLens. Una vez que aparezca la página principal de la aplicación, seleccione **E/S de dispositivo y Entorno.**  Exploraremos cómo los sensores de HoloLens y el entorno circundante afectan a la asignación espacial, el seguimiento y la colocación de hologramas. 

### <a name="surfaces"></a>Superficies

Los reflejos o superficies con acabados reflejados pueden confundir los HoloLens sensores sobre la forma del objeto.  El dispositivo puede interpretar los objetos reflejados en la superficie como entorno cambiante, lo que puede hacer que el dispositivo pierda el seguimiento.  Si las superficies reflejadas están causando desafíos para HoloLens, considere la posibilidad de agregar una pantalla o unas invidentes que se pueden agregar.

Para obtener más información, [vea superficies en un espacio en](/hololens/hololens-environment-considerations#surfaces-in-a-space) HoloLens [consideraciones sobre el entorno](/hololens/hololens-environment-considerations).

### <a name="lighting"></a>Iluminación

HoloLens rendimiento se puede ver afectado negativamente por condiciones de luz muy bajas o muy brillantes.  Los sensores de seguimiento de HoloLens necesitan alrededor de 500-1000 adicionales de luz para funcionar de forma óptima. Puede usar un medidor o una aplicación móvil para medir la cantidad de luz en el espacio.

Para obtener más información, vea [iluminación](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) en [HoloLens consideraciones sobre el entorno](/hololens/hololens-environment-considerations).

## <a name="anchor-fundamentals"></a>Aspectos básicos del anclaje

Para explorar cómo usar Spatial Anchors para alinear hologramas con un espacio físico, seleccione **Anclaje Denfilametals** en la página principal de la aplicación.

En esta parte de la aplicación, exploraremos los siguientes escenarios de usuario:

>[!div class = "checklist"]
> * ¿Qué ocurre cuando no se aplica ningún delimitador a un objeto?
> * Cuando se Spatial Anchors varios objetos para un grupo de objetos .
> * Uso compartido de un delimitador espacial entre varios colaboradores mediante un código QR.
> * Colocación de delimitadores para objetos muy grandes en un espacio.

Para obtener más información, [consulte Spatial Anchors](/windows/mixed-reality/design/spatial-anchors) en la [documentación Mixed Reality](/windows/mixed-reality/design/spatial-anchors) datos.

## <a name="stability-and-fidelity"></a>Estabilidad y fidelidad

En la página principal de la aplicación, seleccione **Estabilidad y fidelidad para** explorar cómo mejorar la estabilidad del holograma.

Exploraremos los siguientes conceptos clave:

>[!div class = "checklist"]
> * [Velocidad de fotogramas](#frame-rate).
> * [Reproducción en fase tardía (LSR).](#late-stage-reprojection-lsr)
> * [Z-fighting](#z-fighting).
> * [Suavizado de alias](#anti-aliasing).

### <a name="frame-rate"></a>Velocidad de fotogramas

Para proporcionar la mejor experiencia de holograma posible, los desarrolladores de aplicaciones deben mantener 60 fotogramas por segundo (FPS).  En esta parte de la aplicación, alterne entre diferentes opciones de recuento de triángulos para experimentar la diferencia con varias velocidades de fotogramas.

![Optimización del recuento de triángulos](images\qf-triangle-count-optimization.png)

Para más información, consulte [velocidad de fotogramas en](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#frame-rate) el artículo estabilidad del [holograma.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="late-stage-reprojection-lsr"></a>Reproducción en fase tardía (LSR)

La reproducción se usa para estabilizar los hologramas a medida que los usuarios se mueven por su espacio.  Pruebe las distintas opciones de reproyecto proporcionadas por esta parte de la aplicación para ver la diferencia en la calidad del holograma.

![Pruebe las distintas opciones de reproducción para experimentar la diferencia.](images\qf-lsr-modes.jpg)

Para obtener información detallada, consulte [la reproducción en](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#reprojection) el artículo [estabilidad del holograma.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="z-fighting"></a>Z-fighting

La Z-fighting se produce cuando la aplicación de realidad mixta no puede distinguir qué objeto está delante del otro.  Observará el parpadeo de los objetos holográficos a medida que se buscan el mismo valor de profundidad z.  Experimente los efectos de z-fighting en la aplicación cambiando la ubicación de un objeto holográfico, el logotipo de una bicicleta en este caso.

![Experimente z-fighting con colocaciones de objetos.](images\qf-z-fighting.jpg)

Para obtener información detallada sobre z-fighting, consulte [habilitación del](/windows/mixed-reality/develop/unity/recommended-settings-for-unity#enable-depth-buffer-sharing) uso compartido del búfer de profundidad en [el artículo configuración recomendada para Unity.](/windows/mixed-reality/develop/unity/recommended-settings-for-unity)

### <a name="anti-aliasing"></a>Suavizado de alias

El suavizado de contorno es una técnica que se usa para suavizar los bordes irregulares en líneas curvas y diagonales en hologramas.  En esta parte de la aplicación, experimente los efectos de los alias en los radios de texto y bicicleta mostrados.  

## <a name="3d-asset-fundamentals"></a>Aspectos básicos de los recursos 3D

En la página principal de la aplicación, seleccione **3D Asset Fundamentals (Aspectos** básicos de los recursos 3D) para explorar cómo optimizar los recursos 3D con el fin de satisfacer el requisito de velocidad de fotogramas y, al mismo tiempo, mantener una alta fidelidad visual.

Exploraremos los siguientes conceptos clave:

>[!div class = "checklist"]
> * [Recuento de triángulos.](#triangle-count)
> * [El sombreador pasa](#shader-passes).
> * [Draw llama a](#draw-calls).
> * [Finalizar .](#finale)

### <a name="triangle-count"></a>Recuento de triángulos

Seleccione el número y la complejidad de los modelos de bicicleta para experimentar la diferencia visual en función de FPS.

![Elija diferentes opciones de recuento de triángulos para ver los efectos en la velocidad de fotogramas.](images\qf-3d-asset-visible-triangles.jpg)

Para más información, consulte proceso [de creación de recursos.](/windows/mixed-reality/design/asset-creation-process)

### <a name="shader-passes"></a>Pases de sombreador

Seleccione el número de bicicletas y las distintas opciones de sombreador para experimentar la diferencia visual en función de FPS.

![Elija diferentes opciones de sombreador para ver los efectos en la velocidad de fotogramas.](images\qf-3d-asset-shader-complexity.jpg)

Para obtener más información, vea [MrTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Llamadas a Draw

Las llamadas a draw son llamadas que consumen muchos recursos a la tarjeta gráfica.  En esta parte de la aplicación, experimente la diferencia visual de primera mano, ya que el número de llamadas a draw afecta a FPS.

![Las llamadas a Draw deben optimizarse para aumentar el rendimiento.](images\qf-3d-asset-draw-calls.jpg)

Consulte [recomendaciones de rendimiento de CPU a GPU.](/windows/mixed-reality/develop/unity/performance-recommendations-for-unity#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Final

Aquí, podemos explorar cuántas bicicletas totalmente optimizadas se pueden mostrar y el nivel de fidelidad posible dadas las técnicas de optimización.

![Técnicas de optimización utilizadas.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Pasos siguientes

Explore otros escenarios de ejemplo de realidad mixta:

   > [!div class="nextstepaction"]
   > [Aplicaciones de ejemplo y características](../features-and-samples.md)