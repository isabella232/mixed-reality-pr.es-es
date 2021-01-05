---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718059"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Plano del evento Begin Play Connected para configurar la función gestos](../images/unreal-hand-tracking-img-09.png)

Después, debe agregar código para suscribirse a los siguientes eventos:

![Plano de gestos de la retención de entrada espacial de Windows, TAP y izquierda gestos ](../images/unreal/key-events.png)
 ![ de manipulación de entradas espaciales de Windows en el panel detalles](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

En OpenXR, se realiza un seguimiento de los eventos de gesto a través de la canalización de entrada. Mediante la interacción con la mano, el dispositivo puede reconocer automáticamente los gestos de pulsar y mantener, pero no los demás. Se denominan asignaciones de selección y control de OpenXRMsftHandInteraction. No es necesario habilitar la suscripción. debe declarar los eventos en configuración del proyecto/motor/entrada, de la siguiente manera:

![Captura de pantalla de las asignaciones de acción de OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

Puede encontrar la función Blueprint en en **entrada espacial de Windows Mixed Reality** y la función de C++ agregando `WindowsMixedRealitySpatialInputFunctionLibrary.h` en el archivo de código que realiza la llamada.

![Capturar movimientos](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeración
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Blueprint

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
Puede habilitar y deshabilitar la captura de gestos con la `CaptureGestures` función. Cuando un gesto habilitado activa eventos de entrada, la función devuelve `true` si la captura de gestos se realizó correctamente y se `false` produce un error.

Blueprint

![Movimientos de captura BP](../images/unreal/capture-gestures-bp.png)

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

Los siguientes son eventos clave, que puede encontrar en Blueprints y C++: ![ eventos de clave.](../images/unreal/key-events.png)

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

