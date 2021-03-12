---
title: Seguimiento de manos y ojos articulados en Unity
description: Obtenga información acerca de las dos formas clave de tomar medidas en su mirada en Unity, gestos de mano y controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, Unity, mira, entrada, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: ac122a0353bc5a35202c9aeba0d27c489b72fd68
ms.sourcegitcommit: 6ae047bf0d78819ee68681f7d9450961efbc8595
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2021
ms.locfileid: "103022877"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Seguimiento de manos y ojos articulados en Unity

HoloLens 2 ha incorporado algunas funcionalidades nuevas y emocionantes, como el seguimiento de la mano y el ojo articulados.

La forma más sencilla de aprovechar la nueva funcionalidad en Unity es a través de MRTK. También hay algunas escenas de ejemplo que le ayudarán a empezar.

* [Introducción a la mano articulada en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/hand-tracking.md)
* [Introducción al seguimiento ocular en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bloques de creación que admiten manos, ojos y otros en MRTK 

MRTK V2 proporciona un conjunto de controles de interfaz de usuario y bloques de creación para ayudarle a acelerar el desarrollo.

|  [![Botón](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) [Botón](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button.md) | [Cuadro de límite](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) del [ ![ cuadro de límite](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box.md) | [Controlador de manipulación](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) del [ ![ controlador de manipulación](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| Un control de botón, que admite varios métodos de entrada, incluido HoloLens2's articulado de la mano | Interfaz de usuario estándar para manipular objetos en el espacio 3D. | Script para manipular objetos con una o dos manos. |
|  [![Claqueta](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) [Claqueta](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate.md) | [![Teclado del sistema](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) [Teclado del sistema](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard.md) | [![Interactuable](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) [Interactuable](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable.md) |
| plano de estilo 2D, que admite el desplazamiento con entrada de mano articulada | Ejemplo de script de uso del teclado del sistema en Unity.  | Un script para que los objetos interactúen con los estados visuales y la compatibilidad con temas. |
|  [![Solucionador](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) [Solucionador](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) | [![Colección de objetos ](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) [Colección de objetos ](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection.md) | [![Información sobre herramientas](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) [Información sobre herramientas](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip.md) |
| Diversos comportamientos de posicionamiento de objetos, como etiquetar, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie | Script para diseñar una matriz de objetos en una forma tridimensional | Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible, que se puede utilizar para etiquetar los controladores de movimiento y el objeto. |
|  [![Barra de aplicaciones](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) [Barra de aplicaciones](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar.md) | [![Punteros](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) [Punteros](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers.md) | [![Visualización de la punta del dedo](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) [Visualización de la punta del dedo](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization.md) |
| Interfaz de usuario para la activación manual del cuadro de límite | Información sobre los distintos tipos de punteros. | La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa |
|  [![Seguimiento ocular: selección de destino](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) [Seguimiento ocular: selección de destino](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-target-selection.md) | [![Seguimiento ocular: navegación](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) [Seguimiento ocular: navegación](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/eye-tracking/eye-tracking-navigation.md) | [![Seguimiento ocular: mapa térmico](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [Seguimiento ocular: mapa térmico](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine los ojos, la voz y la entrada de mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena | Obtenga información sobre Cómo desplazarse automáticamente por el texto o acercar el contenido centrado en función de lo que busca| Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario de MRTK en [esta escena de ejemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Puede encontrar otras escenas de ejemplo en la carpeta **assets/MixedRealityToolkit. examples/demos** del [Kit de herramientas de realidad mixta en github](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Escena de ejemplo](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples.md)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Asignación espacial](spatial-mapping-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Interacción basada en los ojos](../../design/eye-gaze-interaction.md)
* [Seguimiento de los ojos en HoloLens 2](../../design/eye-tracking.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Manos: manipulación directa](../../design/direct-manipulation.md)
* [Manos: gestos](../../design/gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](../../design/point-and-commit.md)
* [Interacciones instintivas](../../design/interaction-fundamentals.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
