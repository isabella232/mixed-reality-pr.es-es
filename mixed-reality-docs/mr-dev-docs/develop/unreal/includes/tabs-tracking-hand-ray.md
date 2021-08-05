---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187513"
---
# <a name="426"></a>[4.26](#tab/426)

Para obtener los datos de los rayos de las manos, debe usar la función Obtener datos del controlador de movimiento de la sección anterior. La estructura devuelta contiene dos parámetros que puede usar para crear un rayo de mano: **Posición** del objetivo y **Rotación del objetivo.** Estos parámetros forman un rayo dirigido por el rayo. Debe tomarlos y buscar un holograma al que apunta.

A continuación se muestra un ejemplo de cómo determinar si un rayo de mano alcanza un widget y establecer un resultado de acierto personalizado:

![Plano técnico de la función de datos get motion controller](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Para usar hand rayas en planos planos, busque cualquiera de las acciones **en Windows Mixed Reality HMD**:

![PRESIÓN de los rayos de la mano](../images/unreal/hand-rays-bp.png)

Para acceder a ellos en C++, incluya `WindowsMixedRealityFunctionLibrary.h` en la parte superior del archivo de código de llamada.

### <a name="enum"></a>Enumeración

También tiene acceso a los casos de entrada **en EHMDInputControllerButtons**, que se puede usar en blueprints:

![Botones del controlador de entrada](../images/unreal/input-controller-buttons.png)

Para obtener acceso en C++, use la `EHMDInputControllerButtons` clase enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:

* **Seleccionar:** evento select desencadenado por el usuario.
    * Se desencadena HoloLens 2 pulsación en el aire, la mirada y la confirmación, o bien al decir "Seleccionar" con la [entrada de voz](../unreal-voice-input.md) habilitada.
* **Ver:** evento Desenlazado desencadenado por el usuario.
    * Se desencadena HoloLens 2 al cerrar los dedos del usuario en un holograma.

Puede acceder al estado de seguimiento de la malla de mano en C++ a través `EHMDTrackingStatus` de la enumeración que se muestra a continuación:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:

* **NotTracked:** la mano no está visible
* **Seguimiento:** se realiza un seguimiento completo de la mano.

### <a name="struct"></a>Estructura

La estructura PointerPoseInfo puede proporcionar información sobre los siguientes datos de la mano:

* **Origen:** origen de la mano
* **Dirección:** dirección de la mano
* **Arriba:** vector superior de la mano
* **Orientación:** cuaternión de orientación
* **Estado de seguimiento:** estado de seguimiento actual

Puede acceder a la estructura PointerPoseInfo a través de planos planos, como se muestra a continuación:

![BP de información de posición de puntero](../images/unreal/pointer-pose-info-bp.png)

O con C++:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Functions

Se puede llamar a todas las funciones que se enumeran a continuación en cada fotograma, lo que permite la supervisión continua.

1. **Obtener información de posición de** puntero devuelve información completa sobre la dirección del rayo de la mano en el marco actual.

Plan:

![Obtener información de posición de puntero](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Is Grasped** devuelve true si la mano se encuentra en el marco actual.

Plan:

![Está en la línea de presión](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Is Select Pressed devuelve** true si el usuario desencadenó Seleccionar en el marco actual.

Plan:

![Is Select Pressed BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Is Button Clicked** devuelve true si el evento o el botón se desencadena en el marco actual.

Plan:

![Clic en el botón BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obtener estado de seguimiento del controlador** devuelve el estado de seguimiento en el marco actual.

Plan:

![Obtener el estado de seguimiento del controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```