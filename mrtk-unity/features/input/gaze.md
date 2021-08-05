---
title: Mirar
description: Docummentation on types of Gaze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Mirada,
ms.openlocfilehash: a9d97ef73a7014a46001cbd42281c5ab28f6cf425dfd7605ce5b3c8c7fc45198
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208442"
---
# <a name="gaze"></a>Mirar

[La](/windows/mixed-reality/gaze) mirada es una forma de entrada que interactúa con el mundo en función de la búsqueda del usuario. La mirada existe en dos tipos diferentes

## <a name="head-gaze"></a>Mirada con la cabeza

Este tipo de mirada se basa en la dirección que mira la cabeza o la cámara. La mirada con la cabeza está activa en sistemas que no admiten la mirada con los ojos o en [casos](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) en los que el hardware puede admitir la mirada con los ojos, pero no se ha realizado el conjunto correcto de permisos y configuración.

La mirada con la cabeza suele asociarse HoloLens interacciones de estilo 1 que implican mirar el objeto colocándolo en el centro del marco holográfico y, a continuación, realizando el gesto de pulsar el aire.

## <a name="eye-gaze"></a>Mirada con ojo

Este tipo de mirada se basa en la mirada del usuario. La mirada con los ojos solo está presente en sistemas que admiten el seguimiento de los ojos. Consulte la documentación [de seguimiento de los](eye-tracking/eye-tracking-main.md) ojos para obtener más información sobre cómo usar la mirada con los ojos.

## <a name="gazeprovider"></a>GazeProvider

Gaze functionality (head and eye) (Funcionalidad de mirada (tanto de la cabeza como de los ojos) la [proporciona GazeProvider.](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) Este proveedor se puede configurar en la sección *Puntero* del perfil del sistema de entrada:

![Punto de entrada de configuración de mirada](../images/input/GazeConfigurationEntrypoint.png)

Al igual que otros orígenes de entrada, el proveedor de mirada interactúa con los objetos de la escena mediante el uso de un puntero (vea este documento para obtener información [sobre punteros).](../../architecture/controllers-pointers-and-focus.md)
En el caso del proveedor de mirada, su puntero se implementa a través de `InternalGazePointer` y no se configura a través de un perfil.

Es posible reemplazar gazeprovider de existencias por  una implementación alternativa cambiando tipo de proveedor de mirada para hacer referencia a una clase diferente que implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).
Por lo general, se recomienda usar GazeProvider (y presentar problemas en al encontrar errores), ya que volver a implementar GazeProvider no es trivial.

### <a name="alternative-platform-provided-gaze-poses"></a>Poses de mirada alternativas proporcionadas por la plataforma

De forma predeterminada, MRTK GazeProvider usa el centro del marco de la cámara como origen de la mirada. Algunas plataformas, como Windows Mixed Reality en HoloLens 2, proporcionan una posición de mirada definida alternativamente. Esto se administra a través de `Use Head Gaze Override` la configuración de la configuración de mirada. Cuando se habilita, se usará la invalidación de mirada alternativa. Cuando se deshabilita, se usará el origen predeterminado del centro de fotogramas. En concreto, para HoloLens 2, el ángulo de mirada se elevará varios grados para tener en cuenta la comodidad del usuario al usar la cabeza para dirigirse.

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

En este ejemplo se muestra cómo obtener vector3 que representa la dirección de la mirada del usuario y el origen (el punto desde el que va la dirección).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
