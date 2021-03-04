---
title: Seguimiento de manos y ojos articulados en Unity
description: Obtenga información acerca de las dos formas clave de tomar medidas en su mirada en Unity, gestos de mano y controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, Unity, mira, entrada, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 8c1ab88358f4218fadce9b7a2a0dbd179b680eab
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759761"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Seguimiento de manos y ojos articulados en Unity

HoloLens 2 ha incorporado algunas funcionalidades nuevas y emocionantes, como el seguimiento de la mano y el ojo articulados.

La forma más sencilla de aprovechar la nueva funcionalidad en Unity es a través de MRTK. También hay algunas escenas de ejemplo que le ayudarán a empezar.

* [Introducción a la mano articulada en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/hand-tracking.md)
* [Introducción al seguimiento ocular en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bloques de creación que admiten manos, ojos y otros en MRTK 

MRTK V2 proporciona un conjunto de controles de interfaz de usuario y bloques de creación para ayudarle a acelerar el desarrollo.

|  [Botón](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) de [ ![ botón](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) | [Cuadro de límite](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) del [ ![ cuadro de límite](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) | [Controlador de manipulación](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) del [ ![ controlador de manipulación](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| Un control de botón, que admite varios métodos de entrada, incluido HoloLens2's articulado de la mano | Interfaz de usuario estándar para manipular objetos en el espacio 3D | Script para manipular objetos con una o dos manos |
|  [ ![ Pizarra Slate](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) | [Teclado del sistema](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) de [ ![ teclado del sistema](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) | Interactuable [ ![ interactuable](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) |
| plano de estilo 2D, que admite el desplazamiento con entrada de mano articulada | Script de ejemplo de uso del teclado del sistema en Unity  | Un script para que los objetos interactúen con los Estados visuales y la compatibilidad con temas |
|  [ ![ Solver de](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) Solver [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) | [Colección de objetos](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) de [ ![ colección de objetos](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) | [Información](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) [ ![ sobre herramientas](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) ToolTip |
| Diversos comportamientos de posicionamiento de objetos, como etiquetar, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie | Script para diseñar una matriz de objetos en una forma tridimensional | Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible, que se puede utilizar para etiquetar los controladores de movimiento y el objeto. |
|  [Barra de aplicación](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) de la [ ![ barra de aplicaciones](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) | [ ![ Punteros punteros](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) | [Visualización del dedo](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) de [ ![ visualización](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) |
| Interfaz de usuario para la activación manual del cuadro de límite | Más información sobre los distintos tipos de punteros | La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa |
|  [ ![ Seguimiento ocular:](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) seguimiento ocular de selección de destino [: selección de destino](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) | [ ![ Seguimiento ocular:](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) [seguimiento ocular de navegación: navegación](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) | [ ![ Seguimiento ocular:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) seguimiento de la vista de mapa térmico [: mapa térmico](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine los ojos, la voz y la entrada de mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena | Obtenga información sobre Cómo desplazarse automáticamente por el texto o acercar el contenido centrado en función de lo que busca| Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario en [esta escena de ejemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)en MRTK.

Puede encontrar otras escenas de ejemplo en la carpeta **assets/MixedRealityToolkit. examples/demos** del [Kit de herramientas de realidad mixta en github](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Escena de ejemplo](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/hand-interaction-examples.md)

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
