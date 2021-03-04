---
title: Mirada en Unity
description: Obtenga información sobre cómo usar la entrada de pág como método principal para que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: miras hacia abajo, a la punta, por la cabeza, el holograma, la realidad mixta, el casco de realidad mixta, el casco de realidad mixta de Windows, el casco de realidad virtual, MRTK, el kit de herramientas de realidad mixta
ms.openlocfilehash: 7602eb27da19dc77e4eab1c1a428dc9a1cf8b252
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759691"
---
# <a name="head-gaze-in-unity"></a>Encabezado de la mirada en Unity

[Miramos](../../design/gaze-and-commit.md) el método principal para que los usuarios tengan como destino los [hologramas](../../discover/hologram.md) que crea la aplicación en [realidad mixta](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Implementación del encabezado de mira

Conceptualmente, para determinar el [encabezado](../../design/gaze-and-commit.md) , puede proyectar un rayo hacia delante desde los auriculares del usuario para ver lo que llega. En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md), concretamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La llamada a [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) le proporciona un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto de colisión 3D y el otro GameObject el toque del rayo de la punta.

### <a name="example-implement-head-gaze"></a>Ejemplo: implementación de la cabeza de mira

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Procedimientos recomendados

Aunque en el ejemplo anterior se activa un solo Raycast desde el bucle de actualización para buscar el destino al que apunta el encabezado del usuario, se recomienda usar un solo objeto para administrar todos los procesos de mirados. La combinación de la lógica de mirada le ahorrará la potencia de procesamiento de la aplicación y limitará la raycasting a una por fotograma.

## <a name="visualizing-head-gaze"></a>Visualización del encabezado

Al igual que con un puntero del mouse en un equipo, debe implementar un [cursor](../../design/cursors.md) que represente el encabezado del usuario. Conocer el contenido de destino de un usuario aumenta la confianza con respecto a la forma en que va a interactuar.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Mira al principio en el kit de herramientas de la realidad mixta 
Puede acceder al encabezado de la mirada desde el [Administrador de entrada](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) en MRTK.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Controladores de movimiento](motion-controllers-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Cámara](camera-in-unity.md)
* [Cursores](../../design/cursors.md)
* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
