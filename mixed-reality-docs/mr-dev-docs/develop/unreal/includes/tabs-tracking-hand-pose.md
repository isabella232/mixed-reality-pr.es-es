---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718015"
---
# <a name="426"></a>[4.26](#tab/426)

La jerarquía se describe mediante `EHandKeypoint` enum:

![Imagen de las opciones de keypoint bluprint](../images/hand-keypoint-bp.png)

Puede obtener todos estos datos de las manos de un usuario mediante la función **Get Motion Controller Data** . Esa función devuelve una estructura **XRMotionControllerData** . A continuación se muestra un script de plano de ejemplo que analiza la estructura XRMotionControllerData para obtener las ubicaciones de unión a mano y dibuja un sistema de coordenadas de depuración en cada ubicación de la Unión.

![Plano de la función de datos de mirada conectada a la función de seguimiento de línea por canal](../images/unreal-hand-tracking-img-03.png)

Es importante comprobar si la estructura es válida y es una mano. De lo contrario, puede obtener un comportamiento indefinido en el acceso a las posiciones, las rotaciones y las matrices de radios.

# <a name="425"></a>[4.25](#tab/425)

La `EWMRHandKeypoint` enumeración describe la jerarquía del hueso de la mano. Puede encontrar cada keypoint de mano enumerado en los planos:

![Mano keypoint BP](../images/hand-keypoint-bp.png)

La enumeración completa de C++ se muestra a continuación:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Puede encontrar los valores numéricos de cada caso de enumeración en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .

### <a name="supporting-hand-tracking"></a>Compatibilidad con el seguimiento de la mano

Puede usar el seguimiento de manos en Blueprints agregando **compatibilidad con** el seguimiento de la mano **> Windows Mixed Reality**:

![Seguimiento de mano BP](../images/unreal/hand-tracking-bp.png)

Esta función devuelve `true` si se admite el seguimiento manual en el dispositivo y `false` si el seguimiento de mano no está disponible.

![Admite el seguimiento de manos BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Incluya `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtención del seguimiento manual

Puede usar **GetHandJointTransform** para devolver datos espaciales desde la mano. Los datos se actualizan cada fotograma, pero si se encuentra dentro de un marco, los valores devueltos se almacenan en caché. No se recomienda tener una lógica pesada en esta función por motivos de rendimiento.

![Obtener transformación Unión a mano](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Este es un desglose de los parámetros de función de GetHandJointTransform:

* **Mano** : puede ser la mano izquierda o derecha.
* **Keypoint** : el hueso de la mano.
* **Transformación** : coordenadas y orientación de la base del hueso. Puede solicitar la base del siguiente hueso para obtener los datos de transformación para el final de un hueso. Un hueso de la sugerencia especial proporciona el final de distal.
* * * Radio: radio de la base del hueso.
* * * Valor devuelto: true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.

