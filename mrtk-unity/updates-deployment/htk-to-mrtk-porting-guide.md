---
title: Actualización desde HoloToolkit
description: Migración de HoloLens Toolkit (HTK) a Mixed Reality Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, HTK,
ms.openlocfilehash: b54445dc5ca7a6c01c968929e243a1fc4ca2d107
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281751"
---
# <a name="upgrading-from-holotoolkit"></a>Actualización desde HoloToolkit

Una guía para ayudarle con la migración de HoloLens Toolkit (HTK) a Mixed Reality Toolkit (MRTK).

## <a name="controller-and-hand-input"></a>Entrada de controlador y mano

### <a name="setup-and-configuration"></a>Instalación y configuración

|         Métodos                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Tipo                      | Eventos específicos para botones, con información de tipo de entrada cuando sea pertinente. | Entrada basada en acciones o gestos, que se pasa a través de eventos. |
| Instalación                     | Coloque InputManager en la escena. | Habilite el sistema de entrada en el perfil [de configuración y](../configuration/mixed-reality-configuration-guide.md) especifique un tipo de sistema de entrada concreto. |
| Configuración             | Configurado en el inspector, en cada script individual de la escena. | Se configura mediante el Mixed Reality del sistema de entrada y su perfil relacionado, que se enumeran a continuación. |

Perfiles relacionados:

* Mixed Reality de asignación de controladores
* Mixed Reality de visualización del controlador
* Mixed Reality perfil de gestos
* Mixed Reality de acciones de entrada
* Mixed Reality de reglas de acción de entrada
* Mixed Reality de puntero

[La configuración del proveedor](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) de mirada se modifica en el objeto Cámara principal de la escena.

Los componentes de soporte técnico de la plataforma (por ejemplo, Windows Mixed Reality Administrador de dispositivos) deben agregarse a los proveedores de datos de sus servicios correspondientes.

### <a name="interface-and-event-mappings"></a>Asignaciones de interfaz y eventos

Algunos eventos ya no tienen eventos únicos y ahora contienen [un MixedRealityInputAction](../features/input/input-actions.md). Estas acciones se especifican en el perfil Acciones de entrada y se asignan a controladores y plataformas específicos en el perfil asignación de controladores. Eventos como `OnInputDown` ahora deben comprobar el tipo MixedRealityInputAction.

Sistemas de entrada relacionados:

* [Información general sobre acciones del usuario](../features/input/overview.md)
* [Eventos de entrada](../features/input/input-events.md)
* [Punteros de entrada](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Asignación de acciones |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Asignado al panel táctil o al control de posición |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Asignado al panel táctil |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Asignado para que se mantenga en el perfil de gestos |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Asignado a los botones del controlador o a la pulsación con la mano |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Asignado a la manipulación en el perfil de gestos |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Asignado a la navegación en el perfil de gestos |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Asignado a la posición del desencadenador |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Asignado a la posición del puntero o a la posición del control |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Asignado a la posición del puntero o a la posición del control |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) y [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Asignado a los distintos botones y botones de controlador |

## <a name="camera"></a>Cámara

|        Métodos                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Elimine MainCamera, agregue MixedRealityCameraParent / MixedRealityCamera / HoloLensCamera prefab a la escena o use Mixed Reality Toolkit > configurar > aplicar Mixed Reality escena Configuración elemento de menú.  | MainCamera primario en MixedRealityPlayspace a través Mixed Reality Toolkit > agregar a la escena y configurar... |
| Configuración             | Configuración de la cámara realizada en la instancia prefab. | Configuración de la cámara configurada en [el Cámara de realidad mixta perfil](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Voz

### <a name="keyword-recognition"></a>Reconocimiento de palabras clave

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Agregue un speechInputSource a la escena. | El servicio keyword (por ejemplo, Windows Speech Input Manager) debe agregarse a los proveedores de datos del sistema de entrada. |
| Configuración             | Las palabras clave reconocidas se configuran en el inspector de SpeechInputSource. | Las palabras clave se configuran en el [Mixed Reality de comandos de voz](../features/input/speech.md). |
| Controladores de eventos            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Dictado

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Agregue una instancia de DictationInputManager a la escena. | La compatibilidad con dictado requiere que el servicio (por ejemplo, Windows de entrada de dictado) se agrega a los proveedores de datos del sistema de entrada. |
| Controladores de eventos            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Reconocimiento espacial/asignación

### <a name="mesh"></a>En malla

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Agregue el objeto prefab SpatialMapping a la escena. | Habilite el sistema de reconocimiento espacial en el perfil de configuración y agregue un observador espacial (por ejemplo, Windows Mixed Reality Observador de malla espacial) a los proveedores de datos del sistema de reconocimiento espacial. |
| Configuración             | Configure la instancia de escena en el inspector. | Configure los valores en el perfil de cada observador espacial. |

### <a name="planes"></a>Aviones

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Use el `SurfaceMeshesToPlanes` script. | Sin implementar todavía. |

### <a name="spatial-understanding"></a>Comprensión espacial

|       Métodos                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Agregue el objeto prefab SpatialUnderstanding a la escena. | Sin implementar todavía. |
| Configuración             | Configure la instancia de escena en el inspector. | Sin implementar todavía. |

## <a name="boundary"></a>Límite

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Agregue el `BoundaryManager` script a la escena. | Habilite el sistema de límites en el perfil de configuración. |
| Configuración             | Configure la instancia de escena en el inspector. | Configure los valores en el perfil Visualización de límites. |

## <a name="sharing"></a>Uso compartido

|             Métodos               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Instalación                     | Servicio de uso compartido: agregue el prefab Uso compartido a la escena. UNet: use el ejemplo SharingWithUNET. | En curso |
| Configuración             | Configure las instancias de escena en el inspector. | En curso |

## <a name="ux"></a>Experiencia de usuario

|         Métodos                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Botón                     | [Objetos interactuables](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Botón](../features/ux-building-blocks/Button.md) |
| Interactuable                     | [Objetos interactuables](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Interactuable](../features/ux-building-blocks/Interactable.md) |
| Cuadro de límite             | [Rectángulo de selección](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Rectángulo de selección](../features/ux-building-blocks/bounding-box.md) |
| Barra de la aplicación             | [Barra de aplicaciones](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Barra de aplicaciones](../features/ux-building-blocks/app-bar.md) |
| Manipulación con una mano (Grb y Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Controlador de manipulación](../features/ux-building-blocks/manipulation-handler.md) |
| Manipulación de dos manos (agarrar, mover, girar o escalar)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Controlador de manipulación](../features/ux-building-blocks/manipulation-handler.md) |
| Teclado             | [Prefab de teclado]() | [Teclado del sistema](../features/ux-building-blocks/system-keyboard.md) |
| Información sobre herramientas             | [Información sobre herramientas](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Información sobre herramientas](../features/ux-building-blocks/tooltip.md) |
| Colección de objetos             | [Colección de objetos](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Colección de objetos](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Utilidades

Algunas utilidades se han conciliado como duplicados con el sistema solver. Si falta alguno de los scripts que necesita, envíe un problema.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Cartelera | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) o [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Solucionador](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Solucionador](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Sistema de diagnóstico](../features/diagnostics/diagnostics-system-getting-started.md) (en el perfil de configuración) |
| NearFade | Integrado en el [sombreador Mixed Reality Toolkit estándar](../features/rendering/mrtk-standard-shader.md) |
