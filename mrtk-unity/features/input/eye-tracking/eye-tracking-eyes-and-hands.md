---
title: Ojos y manos del seguimiento ocular
description: Uso de la orientación con los ojos como puntero principal en combinación con los movimientos de la mano en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143993"
---
# <a name="eyes--hand-interaction"></a>Interacción con los ojos y las manos

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Cómo admitir _movimientos de apariencia y mano_ (mirada con los ojos & gestos de la mano)

En esta página se explica cómo usar la orientación con los ojos como puntero principal en combinación con los movimientos de la mano.
En nuestras demostraciones de seguimiento ocular de [MRTK,](../../example-scenes/eye-tracking-examples-overview.md)se describen varios ejemplos para usar los ojos y las manos, por ejemplo:

- [Selección:](eye-tracking-target-selection.md)examinar el botón holográfico lejano y simplemente realizar un gesto de acercamiento para seleccionarlo rápidamente.
- **Posicionamiento (este artículo):** mueva fluidamente un holograma por la escena con solo mirarlo, acercando el dedo índice y el dedo para agarrarlo y moverlo con la mano.
- [Navegación:](eye-tracking-navigation.md)solo tiene que mirar la ubicación en la que  desea acercar, reducir el dedo índice y el dedo y el dedo, y extraer la mano hacia usted para acercarse.

Tenga en cuenta que MRTK está diseñado actualmente de forma que, a distancia, los rayos de las manos actúan como punteros de foco con prioridad.
Esto significa que los punteros de mirada con la cabeza y los ojos se suprimirán automáticamente una vez que se detecte una mano y se volverán a ver después de decir "Seleccionar".
Sin embargo, puede que esta no sea la manera en que le gustaría interactuar a distancia y, en su lugar, favorecer una interacción simple de "mirada y _confirmación"_ independiente de la presencia de las manos en la vista.

### <a name="how-to-disable-the-hand-ray"></a>Cómo deshabilitar el rayo de mano

Para deshabilitar el puntero de rayo de mano, simplemente quite _"DefaultControllerPointer"_ en la opción de configuración input _-> Pointer_ MRTK.
Para usar los ojos y las manos como se describió anteriormente en la aplicación, asegúrese también de cumplir todos los requisitos para usar el [seguimiento ocular.](eye-tracking-basic-setup.md)

![Cómo quitar el rayo de la mano](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

También puede comprobar cómo se configura el perfil de entrada _EyeTrackingDemoPointerProfile_ del paquete de ejemplo de seguimiento ocular como referencia.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Cómo mantener el puntero de mirada siempre on

Para evitar que los punteros de mirada con la cabeza o los ojos se suprima automáticamente una vez que se detecta una mano, se puede especificar la mirada para controlar si debe estar activa [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o desactivada.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Consulte [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)](eye-tracking-main.md)
