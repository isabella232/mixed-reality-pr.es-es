---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002746"
---
# <a name="425"></a>[4.25](#tab/425)

Para usar rayos de mano en blueprints, busque cualquiera de las acciones en **Windows Mixed Reality HMD**:

![Rayos de mano BP](../images/unreal/hand-rays-bp.png)

Para tener acceso a ellos en C++, incluya `WindowsMixedRealityFunctionLibrary.h` en la parte superior del archivo de código que realiza la llamada.

### <a name="enum"></a>Enumeración

También tiene acceso a los casos de entrada en **EHMDInputControllerButtons**, que se pueden usar en Blueprints:

![Botones del controlador de entrada](../images/unreal/input-controller-buttons.png)

Para el acceso en C++, utilice la `EHMDInputControllerButtons` clase enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:

* **Select** : evento de selección desencadenada por el usuario.
    * Se desencadena en HoloLens 2 con la pulsación aérea, miran y confirman, o bien diciendo "Select" con [entrada de voz](../unreal-voice-input.md) habilitada.
* **Agarre** : evento de agarre desencadenado por el usuario.
    * Se desencadena en HoloLens 2 cerrando los dedos del usuario en un holograma.

Puede tener acceso al estado de seguimiento de la malla de mano en C++ a través de la `EHMDTrackingStatus` enumeración que se muestra a continuación:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:

* **NotTracked** : la mano no es visible
* **Seguimiento** : se realiza un seguimiento completo de la mano

### <a name="struct"></a>Estructura

El struct PointerPoseInfo puede proporcionarle información sobre los siguientes datos de la mano:

* **Origin** : origen de la mano
* **Dirección** : dirección de la mano
* **Vertical** : Vector de la mano
* **Orientación** : cuaternión de orientación
* **Estado de seguimiento** : estado de seguimiento actual

Puede acceder a la estructura PointerPoseInfo a través de blueprints, como se muestra a continuación:

![El puntero representa la información BP](../images/unreal/pointer-pose-info-bp.png)

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

Todas las funciones que se enumeran a continuación se pueden llamar en cada fotograma, lo que permite la supervisión continua.

1. **Obtener** información de la pose de puntero devuelve información completa sobre la dirección del rayo en el marco actual.

Blueprint

![Obtener información de la repostura de puntero](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Se ha captado** devuelve true si la mano se ha captado en el fotograma actual.

Blueprint

![Se ha captado BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. Si **se selecciona, se** devuelve true si el usuario desencadenó SELECT en el marco actual.

Blueprint

![Seleccione BP presionado](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Si se **hace clic** en el botón, devuelve true si el evento o el botón se desencadena en el marco actual.

Blueprint

![Clic en el botón BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obtener estado de seguimiento del controlador** devuelve el estado de seguimiento en el marco actual.

Blueprint

![Obtiene el estado de seguimiento del controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[4.26](#tab/426)

Para obtener los datos de los rayos de mano, debe usar la función get Motion Controller data de la sección anterior. La estructura devuelta contiene dos parámetros que se pueden usar para crear un rayo de mano: **posición de objetivo** y **rotación de objetivos**. Estos parámetros forman un rayo dirigido por el codo. Debe tomarlos y encontrar un holograma al que apunta.

A continuación se muestra un ejemplo de cómo determinar si un rayo de mano alcanza un widget y establece un resultado personalizado de aciertos:

![Plano de la función get Motion Controller Data](../images/unreal-hand-tracking-img-04.png) 