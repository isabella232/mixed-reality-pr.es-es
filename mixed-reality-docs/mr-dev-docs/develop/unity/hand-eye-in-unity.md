---
title: Seguimiento de manos y ojos articulados en Unity
description: Obtenga información sobre las dos formas clave de realizar acciones en la mirada en Unity, los gestos de la mano y los controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, unity, mirada, entrada, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223916"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Seguimiento de manos y ojos articulados en Unity

HoloLens 2 ha introducido algunas funcionalidades nuevas y emocionantes, como el seguimiento de manos y ojos articulados.

La manera más fácil de aprovechar la nueva funcionalidad en Unity es a través de MRTK. También hay algunas escenas de ejemplo que le ayudarán a empezar a trabajar.

* [Introducción a La mano articulada en MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Introducción al seguimiento de los ojos en MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bloques de creación que admiten manos, ojos y otros en MRTK

MRTK v2 proporciona un conjunto de controles de interfaz de usuario y bloques de creación para ayudarle a acelerar el desarrollo.

|  [![Botón](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Botón](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ Rectángulo de selección de](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) rectángulo de [selección](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ Controlador de manipulación del](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) [controlador de manipulación](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Control de botón, que admite varios métodos de entrada, incluida la mano articulada de HoloLens2 | Interfaz de usuario estándar para manipular objetos en el espacio 3D. | Script para manipular objetos con una o dos manos. |
|  [![Claqueta](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Claqueta](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Teclado del sistema](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Teclado del sistema](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Interactuable](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interactuable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| Plano de estilo 2D, que admite el desplazamiento con entrada de mano articulada | Ejemplo de script de uso del teclado del sistema en Unity.  | Un script para que los objetos interactúen con los estados visuales y la compatibilidad con temas. |
|  [![Solucionador](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solucionador](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Colección de objetos ](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Colección de objetos ](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![Información sobre herramientas](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [Información sobre herramientas](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Varios comportamientos de posicionamiento de objetos, como la etiqueta a lo largo, el bloqueo de cuerpo, el tamaño de vista constante y el magnetismo de la superficie | Script para la diseño de una matriz de objetos en una forma tridimensional | Interfaz de usuario de anotación con sistema de anclaje/pivote flexible, que se puede usar para etiquetar controladores de movimiento y objetos. |
|  [![Barra de aplicaciones](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [Barra de aplicaciones](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![Punteros](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Punteros](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Visualización de la punta del dedo](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualización de la punta del dedo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interfaz de usuario para la activación manual de Bounding Box | Información sobre los distintos tipos de punteros. | Asequibilidad visual en el dedo, lo que mejora la confianza para la interacción directa |
|  [![Seguimiento ocular: selección de destino](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Seguimiento ocular: selección de destino](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Seguimiento ocular: navegación](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Seguimiento ocular: navegación](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combine los ojos, la voz y la entrada de mano para seleccionar hologramas en la escena de forma rápida y sencilla. | Obtenga información sobre cómo desplazar texto automáticamente o acercar el contenido centrado en función de lo que está viendo.| Ejemplos de registro, carga y visualización de lo que los usuarios han visto en la aplicación |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario de MRTK en [esta escena de ejemplo](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

Puede encontrar otras escenas de ejemplo [en Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) la **carpeta Assets/MixedRealityToolkit.Examples/Demos.**

[![Escena de ejemplo](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra a la mitad de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

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
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)