---
title: Ojos y manos
description: Uso de la orientación con los ojos como puntero principal en combinación con los movimientos de la mano en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: 37411eb344b4efae03a00bb06a31ce56182cc724d96b2cdcc008f10a66d56011
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224779"
---
# <a name="eyes-and-hands"></a>Ojos y manos

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Cómo admitir _movimientos de apariencia y mano_ (mirada con los ojos & gestos de mano)

En esta página se explica cómo usar la orientación con los ojos como puntero principal en combinación con los movimientos de las manos.
En nuestras demostraciones de seguimiento de los ojos de [MRTK,](../../example-scenes/eye-tracking-examples-overview.md)se describen varios ejemplos para usar los ojos y las manos, por ejemplo:

- [Selección:](eye-tracking-target-selection.md)examinar el botón holográfico lejana y simplemente realizar un gesto de acercamiento para seleccionarlo rápidamente.
- **Posicionamiento (este artículo):** mueva fluidamente un holograma a través de la escena con solo mirarlo, aprete el dedo índice y el dedo para agarrarlo y moverlo con la mano.
- [Navegación:](eye-tracking-navigation.md)basta con mirar la ubicación en la que desea  acercar, reducir el dedo índice y el dedo índice juntos y extraer la mano hacia usted para acercarse.

Tenga en cuenta que MRTK está diseñado actualmente de forma que, a distancia, los rayos de mano actúan como punteros de foco priorizado.
Esto significa que los punteros de mirada con la cabeza y los ojos se suprimirán automáticamente una vez que se detecte una mano y volverán a ser visibles después de decir "Seleccionar".
Sin embargo, puede que esta no sea la manera en que desea interactuar a distancia y prefiere una interacción simple de "mirada y _confirmación"_ independientemente de la presencia de las manos en la vista.

### <a name="how-to-disable-the-hand-ray"></a>Cómo deshabilitar el rayo de mano

Para deshabilitar el puntero de rayo de mano, simplemente quite _"DefaultControllerPointer"_ en la configuración de MRTK input _-> Pointer._
Para usar los ojos y las manos como se ha descrito anteriormente en la aplicación, asegúrese también de cumplir todos los requisitos para usar el [seguimiento de los ojos.](eye-tracking-basic-setup.md)

![Cómo quitar el rayo de mano](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

También puede consultar cómo se configura como referencia el perfil de entrada _EyeTrackingDemoPointerProfile_ del paquete de ejemplo de seguimiento de los ojos.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Cómo mantener el puntero de mirada siempre on

Para evitar que los punteros de mirada con la cabeza o los ojos se suprima automáticamente una vez que se detecta una mano, se puede especificar la mirada para controlar si debe estar activa [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o desactivada.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Consulte [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)](eye-tracking-main.md)
