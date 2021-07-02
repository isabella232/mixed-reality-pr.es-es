---
title: Menú Mano
description: Escena de ejemplo de menú de mano en MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, HandMenu,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177518"
---
# <a name="hand-menu"></a>Menú Mano

![Ejemplo de experiencia de usuario del menú mano](../images/solver/MRTK_UX_HandMenu.png)

Los menús de mano permiten a los usuarios abrir rápidamente la interfaz de usuario adjuntada a mano para las funciones usadas con frecuencia. Para evitar la activación falsa al interactuar con otros objetos, el menú de mano proporciona opciones como "Requerir mano plana" y "Usar activación de mirada". Se recomienda usar estas opciones para evitar la activación no deseada.

## <a name="hand-menu-examples"></a>Ejemplos de menú de mano

**HandMenuExamples.unity** scene está en ``MRTK/Examples/Demos/HandTracking/Scenes`` la carpeta . Cuando se ejecuta, la escena solo activará el tipo de menú seleccionado actualmente.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

Puede encontrar estos elementos prefabs del menú de la mano en ``MRTK/Examples/Demos/HandTracking/Prefabs`` la carpeta .

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop y HandMenu_Medium_HideOnHandDrop

Estos dos ejemplos simplemente activan y desactivan el objeto MenuContent para mostrar y ocultar el menú en el evento **OnFirstHandDetected()** y **OnLastHandLost().**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

En el caso de los menús más complejos que requieren más tiempo de interacción, se recomienda bloquear el menú. En este ejemplo, el usuario puede agarrar y extraer para bloquear el menú, además de activar y desactivar menuContent en los eventos **OnFirstHandDetected()** y **OnLastHandLost().**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

La placa trasera `ManipulationHandler` hace que sea fácil de agarrar y mover. **En el evento Manipulation Started,** **SolverHandler.UpdateSolvers** se desactiva para bloquear el menú. Además, muestra el botón **Cerrar para** permitir que el usuario cierre el menú cuando finalice la tarea. En el evento **Manipulation Ended,** llama a **HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine** para permitir que el usuario vuelva a poner el menú a mano al elevar y mirar la mano.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

**El** botón Cerrar vuelve a **activar SolverHandler.UpdateSolvers** y oculta **menuContent.**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Este ejemplo es similar a HandMenu_Large_WorldLock_On_GrabAndPull. La única diferencia es que el menú se bloqueará automáticamente al colocarse a mano. Esto se hace simplemente sin ocultar el evento MenuContent en **OnLastHandLost().** El & de extracción es el mismo que HandMenu_Large_WorldLock_On_GrabAndPull ejemplo.

## <a name="scripts"></a>Scripts

El comportamiento proporciona un solucionador que restringe el objeto de seguimiento a una región segura para el contenido restringido a mano (como la interfaz de usuario de la [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) mano, menús, etc.). Caja fuerte regiones se consideran áreas que no se cruzan con la mano. También se incluye una clase derivada de llamada para mostrar un comportamiento común de activar el objeto de seguimiento del solucionador cuando la mano se enfrenta [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) al usuario.

Consulte las sugerencias de herramientas disponibles para cada [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) propiedad para obtener documentación adicional. A continuación se definen algunas propiedades con más detalle.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **Caja fuerte zona segura:** la zona segura especifica dónde restringir el contenido. Se recomienda colocar contenido en el lado de Ulnar para evitar superponerse con la mano y mejorar la calidad de la interacción. Caja fuerte se calculan tomando la orientación de las manos proyectada en un plano ortogonal a la vista de la cámara y la proyección de rayos en un rectángulo delimitador alrededor de las manos. Caja fuerte se definen para trabajar con , [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) pero también funciona con otros tipos de controlador. Se recomienda explorar lo que representa cada zona segura en distintos tipos de controlador.

* **Seguimiento de la mano hasta la cámara orientada** Con esta opción activa, el solucionador seguirá la rotación de las manos hasta que el menú esté lo suficientemente alineado con la mirada, momento en el que se enfrenta a la cámara. Esto funciona cambiando SolverRotationBehavior en HandConstraintSolver, de LookAtTrackedObject a LookAtMainCamera a medida que varía el ángulo GazeAlignment con el solucionador.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **Eventos de activación:** [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) actualmente, desencadena cuatro eventos de activación. Estos eventos se pueden usar en muchas combinaciones diferentes para crear comportamientos únicos. Consulte la escena HandBasedMenuExample en para obtener [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) ejemplos de estos `MRTK/Examples/Demos/HandTracking/Scenes/` comportamientos.

  * *OnHandActivate:* se desencadena cuando una mano satisface el método IsHandActive.
  * *OnHandDeactivate:* se desencadena cuando el método IsHandActive ya no se cumple.
  * *OnFirstHandDetected:* se produce cuando el estado de seguimiento de las manos cambia de ninguna mano a la vista.
  * *OnLastHandLost:* se produce cuando el estado de seguimiento de las manos cambia de al menos una mano en vista a ninguna mano a la vista.

* Lógica de **activación/desactivación** del solucionador: actualmente, la recomendación para activar y desactivar la lógica es hacerlo mediante el uso del valor UpdateSolver de SolverHandler, en lugar de deshabilitar o habilitar el [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) objeto . Esto se puede ver en la escena de ejemplo a través de los enlaces basados en editor desencadenados después de los eventos ManipulationHandler "OnManipulationStarted/Ended" del menú adjunto.

  * *Detener* la lógica de restricción manual: al intentar establecer el objeto restringido con la mano para detenerse (además de no ejecutar la lógica de activación o desactivación), establezca UpdateSolver en False en lugar de deshabilitar HandConstraintPalmUp.
    * Si desea habilitar la lógica Reattach basada en mirada (o incluso no basada en mirada), esto se sigue llamando a la función HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine(). Esto desencadenará una corrotina que, a continuación, continúa con la comprobación de si se cumplen los criterios "IsValidController" y establecerá UpdateSolver en True una vez que sea (o el objeto está deshabilitado).
  * *Iniciar* la lógica de restricción de mano: al intentar establecer el objeto restringido con la mano para empezar a seguir de nuevo la mano (en función de si cumple los criterios de activación), establezca UpdateSolver de SolverHandler en true.

* Volver a adjuntar **lógica:** actualmente, es capaz de volver a asociar automáticamente el objeto de destino al punto al que se realiza el seguimiento, independientemente de si [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) updateSolver de SolverHandler es True o no. Esto se hace mediante una llamada a la función StartWorldLockReattachCheckCoroutine() de HandConstraintPalmUp, después de que se haya bloqueado el mundo (que, en este caso, está estableciendo eficazmente UpdateSolver de SolverHandler en False).

## <a name="see-also"></a>Consulte también

* [Button](button.md)
* [Menú Cercano](near-menu.md)
