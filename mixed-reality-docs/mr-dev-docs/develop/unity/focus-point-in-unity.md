---
title: Punto de enfoque en Unity
description: Aprenda a ajustar manualmente la estabilidad del holograma en Unity estableciendo el punto de enfoque para HoloLens y Windows Mixed Reality cascos envolventes.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, plano de enfoque, plano de estabilización, punto de estabilización, reproducción, LSR, búfer de profundidad, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 91fba310cf86f145174512c4c1e23d69907d2f57f48f3fe1992b417eb283235f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203597"
---
# <a name="focus-point-in-unity"></a>Punto de enfoque en Unity

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

Use el [punto de](../platform-capabilities-and-apis/hologram-stability.md#reprojection) enfoque para proporcionar HoloLens sugerencia sobre cómo estabilizar mejor los hologramas que se muestran actualmente.

Si desea establecer el punto de enfoque en Unity, debe establecerse cada fotograma mediante *HolographicSettings.SetFocusPointForFrame().* Cuando no se establece el punto de enfoque para un marco, se usa el plano de estabilización predeterminado.

> [!NOTE]
> De forma predeterminada, los nuevos proyectos de Unity tienen establecida la opción "Habilitar uso compartido de búfer de profundidad".  Con esta opción, una aplicación de Unity que se ejecute en un casco de escritorio envolvente o en un HoloLens que ejecute la actualización de abril de 2018 de Windows 10 (RS4) o posterior, envía el búfer de profundidad a Windows para optimizar la estabilidad del holograma automáticamente, sin que la aplicación especifique un punto de enfoque:
> * En un casco de escritorio envolvente, esto habilitará la reproducción basada en profundidad por píxel.
> * En un HoloLens la actualización Windows 10 abril de 2018 o posterior, se analizará el búfer de profundidad para elegir automáticamente un plano de estabilización óptimo.
>
> Cualquiera de los enfoques debe proporcionar una calidad de imagen aún mejor sin que la aplicación haga un trabajo explícito para seleccionar un punto de enfoque para cada fotograma.  Tenga en cuenta que si proporciona un punto de enfoque manualmente, invalidará el comportamiento automático descrito anteriormente y normalmente reducirá la estabilidad del holograma.  Por lo general, solo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en un HoloLens que aún no se ha actualizado a la actualización de Windows 10 abril de 2018.

### <a name="example"></a>Ejemplo

Hay muchas maneras de establecer el punto de enfoque, como sugieren las sobrecargas disponibles en la *función estática SetFocusPointForFrame.* A continuación se muestra un ejemplo sencillo para establecer el plano de foco en el objeto proporcionado para cada fotograma:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> El código simple anterior puede reducir la estabilidad del holograma si el objeto enfocado termina detrás del usuario. Por lo general, se recomienda establecer Habilitar el uso compartido **[del búfer de](camera-in-unity.md#sharing-depth-buffers)** profundidad en lugar de especificar manualmente un punto de enfoque.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra en medio de la exploración de las API y las funcionalidades de Mixed Reality plataforma. Desde aquí, puede continuar con el siguiente tema:

> [!div class="nextstepaction"]
> [Pérdida de seguimiento](tracking-loss-in-unity.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en HoloLens o Windows Mixed Reality cascos envolventes](../platform-capabilities-and-apis/using-visual-studio.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.

### <a name="see-also"></a>Consulte también

* [Plano de estabilización](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
