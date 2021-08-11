---
title: Pulsación para situar
description: Documentación de TapToPlace en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, Tap to Place
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198323"
---
# <a name="tap-to-place"></a>Pulsación para situar

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

Tap to Place (Pulsar para situar) es un componente de interacción lejana que se usa para situar un objeto de juego en la superficie. Este componente resulta útil para situar objetos en una malla espacial. Tap to Place usa una combinación de dos clics y el movimiento de la cabeza para situar un objeto. Un clic para iniciar la colocación, el movimiento de la cabeza para controlar la posición del objeto y un clic para situar el objeto en la escena.

## <a name="using-tap-to-place"></a>Uso de Tap to Place

1. Configure la escena.
    - Cree un nuevo proyecto de Unity.
    - Para agregar MRTK a la escena, vaya a **Mixed Reality Toolkit** > **Add to Scene and Configure** (Agregar a la escena y configurar).
    > [!NOTE]
    > Tap to Place usa clics controlados por el sistema de entrada de MRTK, pero también se puede controlar sin clics, consulte la sección Capacidad de configuración del código de Tap To Place más adelante.
    - Agregue un cubo a la escena, cambie la escala a 0,2 y cambie la posición a (0, 0, 0,7).
1. Asocie [Tap to Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) a un objeto de juego con un colisionador.

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Cuando se agregue el componente Tap to Place, también se asociará un controlador del solucionador. Tap to Place se deriva de la clase [Solver](solver.md), que requiere un controlador del solucionador. La posición de un objeto Tap to Place se calcula en relación con `TrackedTargetType` dentro del controlador del solucionador. De manera predeterminada, Head es `TrackedTargetType`; es decir, cuando se mueve la cabeza, el objeto la sigue si está seleccionado.  Además, `TrackedTargetType` se puede establecer en Controller Ray (Rayo de controlador), que hace que el objeto siga al controlador. El primer grupo de propiedades del inspector de Tap to Place es [Common Solver Properties](solver.md#common-solver-properties) (Propiedades comunes del solucionador).  
    > [!IMPORTANT]
    > Tap to Place es un solucionador independiente y no se puede encadenar con otros solucionadores. No se puede encadenar porque solverHandler.UpdateSolvers se usa para actualizar la posición del objeto mientras se está situando.
    - Propiedades de Tap to Place:
        - `Auto Start`: Si está activada, el solucionador Tap to Place comenzará a controlar la posición del objeto de juego que se va a situar. El objeto comenzará de inmediato a seguir a TrackedTargetType (Head o Controller Ray). Este valor debe modificarse antes de que se invoque Start() para que surta cualquier efecto.
        - `Default Placement Distance`: La distancia predeterminada (en metros) a la que se situará frente a un objeto en relación con TrackedTargetType en SolverHandler. El objeto de juego se situará a la distancia de colocación predeterminada si el raycast no alcanza una superficie.
        - `Max Raycast Distance`: Distancia máxima (en metros) para el raycast, según el origen de "TrackedTargetType". Este raycast busca una superficie donde situar un objeto seleccionado.
        - `UseDefaultSurfaceNormalOffset`: Esta propiedad está activada de manera predeterminada, se asegura de que el objeto que se está situando esté alineado en una superficie. Si esta propiedad está activada, se aplicará el desplazamiento normal de la superficie predeterminado, en lugar de cualquier valor especificado para la propiedad `SurfaceNormalOffset`. Si está desactivada, se aplicará el valor de `SurfaceNormalOffset`. El desplazamiento normal de la superficie predeterminado son las extensiones del colisionador a lo largo del eje Z.
        - `Surface Normal Offset`: Distancia entre el centro del objeto de juego que se va a situar y una superficie a lo largo de la normal de la superficie, si el raycast alcanza una superficie. Esta propiedad solo se aplica a un objeto si la propiedad `UseDefaultSurfaceNormalOffset` está desactivada.
        - `Keep Orientation Vertical`: Si está activada, el objeto de juego que se va a situar permanecerá vertical y en línea con Vector3.up.
        - `Rotate According to Surface`: Si está desactivada, el objeto de juego que se va a situar no cambiará su rotación según el impacto en la superficie.  El objeto permanecerá orientado a la cámara mientras IsBeingPlaced sea verdadero.
        - `Magnetic Surfaces`: Matriz de LayerMasks para ejecutar desde la prioridad más alta a la más baja. La primera máscara de capas para proporcionar un impacto de raycast se usará para los cálculos de posición.
        - `Debug Enabled`: Si está activada y en el editor de Unity, la normal del impacto del raycast se dibujará en amarillo. La depuración habilitada resulta útil cuando `RotateAccordingToSurface` está activada, ya que dibuja la normal de la superficie alcanzada, lo que explica visualmente por qué el objeto se encuentra en su orientación actual.
        - `On Placing Started`: Este evento se desencadena una vez cuando se selecciona el objeto de juego que se va a situar.
        - `On Placing Stopped`: Este evento se desencadena una vez cuando se anula la selección del objeto de juego que se ha situado.

1. Pruebe el comportamiento de Tap to Place en el editor.
    - Presione el botón de reproducción y mantenga presionada la barra espaciador para mostrar una mano de simulación de entrada.
    - Mueva la mano hasta que el cubo esté en el foco y simule un clic con la mano de simulación de entrada haciendo clic con el mouse izquierdo.
        - Si no hay colisionadores en la escena, el objeto seguirá a `TrackedTargetType` en el `Default Placement Distance` definido.
    - El objeto seguirá el movimiento de `TrackedTargetType` después de la selección. Para simular el movimiento de la cabeza en el editor, presione las teclas W, A, S, D. Para cambiar la rotación de la cabeza, haga clic y mantenga presionado el mouse derecho.
    - Para detener la colocación del objeto, vuelva a hacer clic.  No es necesario que el objeto esté en el foco para hacer clic para detener la colocación. El foco solo es necesario para el clic inicial que inicia el proceso de colocación.

    `TrackedTargetType`: Head (valor predeterminado) |  `TrackedTargetType`: Controller Ray
    :-------------------------:|:-------------------------:
    ![Rayo de control de la cabeza de simulación de entrada de Tap to Place](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Rayo del controlador de simulación de entrada de Tap to Place 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Capacidad de configuración del código de Tap To Place

El tiempo de selección de objetos de Tap to Place también se puede controlar a través de `StartPlacement()` y `StopPlacement()`, en lugar de requerir un evento de clic. Esta funcionalidad es útil para escribir pruebas, y proporciona un método alternativo para situar un objeto en el editor sin usar el sistema de entrada de MRTK.

1. Cree un objeto de juego vacío.
1. Cree y asocie el siguiente script de ejemplo al objeto de juego vacío.

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. En modo de reproducción, presione la *tecla U* para empezar a situar el cubo.
1. Presione la *tecla I* para detener la colocación.

## <a name="tap-to-place-example-scene"></a>Escena de ejemplo de Tap to Place

La escena de ejemplo de Tap to Place consta de cuatro objetos que se puedan situar, cada uno con una configuración diferente. La escena de ejemplo contiene paredes para mostrar los comportamientos de colocación en la superficie, que están deshabilitados de manera predeterminada en la jerarquía. La escena de ejemplo se puede encontrar en el paquete de Unity Microsoft.MixedReality.Toolkit.Unity.Examples que se encuentra en la [página de la versión](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). La ubicación de la escena es: *MRTK. Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*.

![Ejemplos de Tap to Place](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Vea también

- [Solucionadores](solver.md)
- [Reconocimiento espacial](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Simulación de entrada](../../input-simulation/input-simulation-service.md)
- [Seguimiento de manos](../../input/hand-tracking.md)
- [Gaze](../../input/gaze.md)
