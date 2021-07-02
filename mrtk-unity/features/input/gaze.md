---
title: Mirar
description: Docummentation on types of Gaze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Gaze,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176917"
---
# <a name="gaze"></a>Mirar

[La](/windows/mixed-reality/gaze) mirada es una forma de entrada que interactúa con el mundo en función de dónde esté mirando el usuario. La mirada existe en dos tipos diferentes

## <a name="head-gaze"></a>Mirada con la cabeza

Este tipo de mirada se basa en la dirección que mira la cabeza o la cámara. La mirada con la cabeza está activa en sistemas que no admiten la mirada con los ojos o en [casos](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) en los que el hardware puede admitir la mirada con los ojos, pero no se ha realizado el conjunto correcto de permisos y configuración.

La mirada con la cabeza suele asociarse HoloLens interacciones de estilo 1 que implican mirar el objeto colocándolo en el centro del marco holográfico y, a continuación, realizando el gesto de pulsar en el aire.

## <a name="eye-gaze"></a>Mirada con ojo

Este tipo de mirada se basa en la mirada del usuario. La mirada con los ojos solo está presente en sistemas que admiten el seguimiento ocular. Consulte la documentación [de seguimiento de los](eye-tracking/eye-tracking-main.md) ojos para obtener más información sobre cómo usar la mirada con los ojos.

## <a name="gazeprovider"></a>GazeProvider

Gaze functionality (head and eye) (Funcionalidad de mirada (tanto la cabeza como el ojo) la [proporciona GazeProvider.](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) Este proveedor se puede configurar en la sección *Puntero* del perfil del sistema de entrada:

![Punto de entrada de configuración de mirada](../images/input/GazeConfigurationEntrypoint.png)

Al igual que otros orígenes de entrada, el proveedor de mirada interactúa con los objetos de la escena mediante el uso de un puntero (vea este documento para obtener información [sobre punteros).](../../architecture/controllers-pointers-and-focus.md)
En el caso del proveedor de mirada, su puntero se implementa a través `InternalGazePointer` de y no se configura a través de un perfil.

Es posible reemplazar gazeprovider de acciones por  una implementación alternativa cambiando tipo de proveedor de mirada para hacer referencia a una clase diferente que implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).
Por lo general, se recomienda usar GazeProvider (y presentar problemas al encontrar errores), ya que volver a implementar GazeProvider no es trivial.

### <a name="alternative-platform-provided-gaze-poses"></a>Posturas alternativas de mirada proporcionadas por la plataforma

De forma predeterminada, MRTK GazeProvider usa el centro del marco de la cámara como origen de la mirada. Algunas plataformas, como Windows Mixed Reality en HoloLens 2, proporcionan una posición de mirada definida alternativamente. Esto se administra a través de `Use Head Gaze Override` la configuración en la configuración de mirada. Cuando se habilita, se usará la invalidación de mirada alternativa. Cuando se deshabilita, se usará el origen del centro de marco predeterminado. En concreto, para HoloLens 2, el ángulo de mirada se elevará varios grados para tener en cuenta la comodidad del usuario al usar la cabeza para la orientación.

## <a name="usage"></a>Uso

### <a name="how-get-the-current-gaze-target"></a>Cómo obtener el destino de mirada actual

En este ejemplo se muestra cómo obtener el objeto de juego actual que es el objetivo de la mirada del usuario.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>Cómo obtener la dirección y el origen de la mirada actuales

En este ejemplo se muestra cómo obtener vector3 que representa la dirección de la mirada del usuario y el origen (el punto desde el que se va la dirección).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
