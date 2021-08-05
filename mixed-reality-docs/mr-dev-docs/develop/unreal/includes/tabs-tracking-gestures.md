---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187507"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Plano técnico de la reproducción de inicio de eventos conectada para configurar la función de gestos](../images/unreal-hand-tracking-img-09.png)

A continuación, debe agregar código para suscribirse a los siguientes eventos:

![Plano técnico de Windows movimientos de manipulación de entrada espacial, pulsación y manipulación izquierda Captura de pantalla Windows opciones de gesto de pulsar en la entrada espacial en el ](../images/unreal/key-events.png)
 ![ panel de detalles](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

En OpenXR, se realiza un seguimiento de los eventos de gestos a través de la canalización de entrada. Mediante la interacción con la mano, el dispositivo puede reconocer automáticamente los gestos de pulsar y mantener presionados, pero no los demás. Se denominan OpenXRMsftHandInteraction Select y Asignaciones de control. No es necesario habilitar la suscripción, debe declarar los eventos en Project Configuración/Engine/Input, del mismo modo:

![Captura de pantalla de las asignaciones de acciones de OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

Puede encontrar la función Blueprint en en **Windows Mixed Reality Entrada** espacial y la función de C++ agregando en el archivo de código `WindowsMixedRealitySpatialInputFunctionLibrary.h` de llamada.

![Gestos de captura](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeración
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Plan:

![Tipo de gesto](../images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Función
Puede habilitar y deshabilitar la captura de gestos con la `CaptureGestures` función . Cuando un gesto habilitado activa eventos de entrada, la función devuelve si la captura de gestos se ha producido correctamente y si `true` `false` se produce un error.

Plan:

![Captura de gestos bp](../images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

Los siguientes son eventos clave, que puede encontrar en Planos técnico y C++: ![ Eventos clave](../images/unreal/key-events.png)

![Eventos clave 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

