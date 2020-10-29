---
title: Punto de enfoque en Unity
description: Ajuste manual de la estabilidad de holograma en Unity estableciendo el punto de enfoque
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, plano de enfoque, plano de estabilización, punto de estabilización, Reproyección, LSR, búfer de profundidad
ms.openlocfilehash: 4d8c8a232d12a8d6f0a7694fbc0ed8f66395163a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691244"
---
# <a name="focus-point-in-unity"></a>Punto de enfoque en Unity

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo** : *HolographicSettings*

Se puede establecer el [punto de enfoque](../platform-capabilities-and-apis/hologram-stability.md#reprojection) para proporcionar a HoloLens una sugerencia sobre cómo realizar mejor la estabilización en los hologramas que se muestran actualmente.

Si desea establecer el punto de enfoque en Unity, debe establecer cada fotograma mediante *HolographicSettings. SetFocusPointForFrame ()* . Si no se establece el punto de enfoque para un marco, se usará el plano de estabilización predeterminado.

> [!NOTE]
> De forma predeterminada, los nuevos proyectos de Unity tienen establecida la opción "habilitar el uso compartido del búfer de profundidad".  Con esta opción, una aplicación de Unity que se ejecute en un casco de escritorio envolvente o en una HoloLens que ejecute la actualización 2018 de abril de Windows 10 (RS4) o posterior enviará el búfer de profundidad a Windows para optimizar la estabilidad del holograma automáticamente, sin que la aplicación especifique un punto de enfoque:
> * En un casco de escritorio envolvente, esto habilitará la Reproyección basada en profundidad por píxel.
> * En una HoloLens que ejecute la actualización de abril de 2018 de Windows 10 o posterior, se analizará el búfer de profundidad para elegir un plano de estabilización óptimo automáticamente.
>
> Cualquier enfoque debe proporcionar una calidad de imagen incluso mejor sin que la aplicación proporcione un trabajo explícito para seleccionar un punto de enfoque para cada fotograma.  Tenga en cuenta que si proporciona un punto de enfoque manualmente, se invalidará el comportamiento automático descrito anteriormente y se reducirá la estabilidad del holograma.  Por lo general, solo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en una HoloLens que todavía no se ha actualizado a la actualización 2018 de abril de Windows 10.

### <a name="example"></a>Ejemplo

Hay muchas maneras de establecer el punto de enfoque, como se sugiere por las sobrecargas disponibles en la función estática *SetFocusPointForFrame* . A continuación se muestra un ejemplo sencillo para establecer el plano de enfoque en el objeto proporcionado para cada fotograma:

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

Tenga en cuenta que el código anterior puede acabar reduciendo la estabilidad del holograma si el objeto que tiene el foco termina detrás del usuario.  Este es el motivo por el que normalmente debería establecer "habilitar el uso compartido del búfer de profundidad" en lugar de especificar manualmente un punto de enfoque.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede continuar con el tema siguiente:

> [!div class="nextstepaction"]
> [Pérdida de seguimiento](tracking-loss-in-unity.md)

O ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en HoloLens o con auriculares de Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)

Siempre puede volver a los puntos de [control de desarrollo de Unity](unity-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.

### <a name="see-also"></a>Consulte también
* [Plano de estabilización](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
