---
title: Seguimiento de manos y ojos articulados en Unity
description: Obtenga información acerca de las dos formas clave de tomar medidas en su mirada en Unity, gestos de mano y controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, Unity, mira, entrada, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 4c704677a78fee02b9da9d0db9bc2966ab6b3724
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008964"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Seguimiento de manos y ojos articulados en Unity

HoloLens 2 ha incorporado algunas funcionalidades nuevas y emocionantes, como el seguimiento de la mano y el ojo articulados.

La forma más sencilla de aprovechar la nueva funcionalidad en Unity es a través de MRTK. También hay algunas escenas de ejemplo que le ayudarán a empezar.

* [Introducción a la mano articulada en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introducción al seguimiento ocular en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bloques de creación que admiten manos, ojos y otros en MRTK 

MRTK V2 proporciona un conjunto de controles de interfaz de usuario y bloques de creación para ayudarle a acelerar el desarrollo.

|  [Botón](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) de [ ![ botón](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [Cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) del [ ![ cuadro de límite](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Controlador de manipulación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) del [ ![ controlador de manipulación](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Un control de botón, que admite varios métodos de entrada, incluido HoloLens2's articulado de la mano | Interfaz de usuario estándar para manipular objetos en el espacio 3D | Script para manipular objetos con una o dos manos |
|  [ ![ Pizarra Slate](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [Teclado del sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) de [ ![ teclado del sistema](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | Interactuable [ ![ interactuable](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| plano de estilo 2D, que admite el desplazamiento con entrada de mano articulada | Script de ejemplo de uso del teclado del sistema en Unity  | Un script para que los objetos interactúen con los Estados visuales y la compatibilidad con temas |
|  [ ![ Solver de](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) Solver [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) de [ ![ colección de objetos](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Información](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![ sobre herramientas](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) ToolTip |
| Diversos comportamientos de posicionamiento de objetos, como etiquetar, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie | Script para diseñar una matriz de objetos en una forma tridimensional | Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible, que se puede utilizar para etiquetar los controladores de movimiento y el objeto. |
|  [Barra de aplicación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) de la [ ![ barra de aplicaciones](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [ ![ Punteros punteros](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [Visualización del dedo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) de [ ![ visualización](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Interfaz de usuario para la activación manual del cuadro de límite | Más información sobre los distintos tipos de punteros | La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa |
|  [ ![ Seguimiento ocular:](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) seguimiento ocular de selección de destino [: selección de destino](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [ ![ Seguimiento ocular:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) [seguimiento ocular de navegación: navegación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [ ![ Seguimiento ocular:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) seguimiento de la vista de mapa térmico [: mapa térmico](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine los ojos, la voz y la entrada de mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena | Obtenga información sobre Cómo desplazarse automáticamente por el texto o acercar el contenido centrado en función de lo que busca| Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario en [esta escena de ejemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)en MRTK.

Puede encontrar otras escenas de ejemplo en la carpeta **assets/MixedRealityToolkit. examples/demos** del [Kit de herramientas de realidad mixta en github](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![Escena de ejemplo](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

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
