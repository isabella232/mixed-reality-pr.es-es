---
ms.openlocfilehash: ec1246085989b4b157504e9b8551694d6116e6f08789fa669200e5425ef75cc6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187508"
---
# <a name="426"></a>[4.26](#tab/426)

La jerarquía se describe mediante `EHandKeypoint` enumeración:

![Imagen de las opciones de huella digital del punto de tecla de mano](../images/hand-keypoint-bp.png)

Puede obtener todos estos datos de las manos de un usuario mediante la **función Obtener datos del controlador de** movimiento. Esa función devuelve una **estructura XRMotionControllerData.** A continuación se muestra un script de plano técnico de ejemplo que analiza la estructura XRMotionControllerData para obtener ubicaciones conjuntas de mano y dibuja un sistema de coordenadas de depuración en la ubicación de cada unión.

![Plano técnico de la función get gaze data conectada al seguimiento de línea por función de canal](../images/unreal-hand-tracking-img-03.png)

Es importante comprobar si la estructura es válida y si es una mano. De lo contrario, puede obtener un comportamiento indefinido en el acceso a posiciones, rotaciones y matrices radii.

# <a name="425"></a>[4.25](#tab/425)

La `EWMRHandKeypoint` enumeración describe la jerarquía de jerarquías de la mano. Puede encontrar cada punto de clave de mano que se muestra en los planos técnico:

![Punto de tecla de mano BP](../images/hand-keypoint-bp.png)

A continuación se muestra la enumeración completa de C++:
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

Puede encontrar los valores numéricos de cada caso de enumeración en [la Windows. Tabla Perception.People.HandJointKind.](/uwp/api/windows.perception.people.handjointkind)

### <a name="supporting-hand-tracking"></a>Compatibilidad con el seguimiento de manos

Puede usar el seguimiento de manos en Planos técnico agregando **Supports Hand Tracking** from Hand Tracking **> Windows Mixed Reality**:

![Bp de seguimiento de manos](../images/unreal/hand-tracking-bp.png)

Esta función devuelve `true` si se admite el seguimiento de manos en el dispositivo y si el seguimiento de manos no está `false` disponible.

![Admite la bp de seguimiento de manos](../images/unreal/supports-hand-tracking-bp.png)

C++:

Incluya `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtención del seguimiento a mano

Puede usar **GetHandJointTransform para** devolver datos espaciales de la mano. Los datos actualiza cada fotograma, pero si está dentro de un marco, los valores devueltos se almacenan en caché. No se recomienda tener una lógica pesada en esta función por motivos de rendimiento.

![Get Hand Joint Transform](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Este es un desglose de los parámetros de función de GetHandJointTransform:

* **Mano:** puede ser la mano izquierda o derecha de los usuarios.
* **Punto de clave:** el dedo de la mano.
* **Transformación:** coordenadas y orientación de la base del aire. Puede solicitar la base del siguiente tejido para obtener los datos de transformación para el final de un desenlazón. Una propina especial proporciona el final del distal.
* **Radio: radio de la base del póreo.
* **Valor devuelto: true si se realiza el seguimiento de este marco, false si no se realiza el seguimiento de los restos.