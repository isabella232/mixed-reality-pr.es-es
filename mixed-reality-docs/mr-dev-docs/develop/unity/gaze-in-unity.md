---
title: Mirada en Unity
description: Fijamente es una forma principal de que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: miras hacia abajo, a la punta, por la cabeza, el holograma, la realidad mixta, el casco de realidad mixta, el casco de realidad mixta de Windows, el casco de realidad virtual, MRTK, el kit de herramientas de realidad mixta
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677514"
---
# <a name="head-gaze-in-unity"></a>Encabezado de la mirada en Unity

[Fijamente](../../design/gaze-and-commit.md) es una forma principal de que los usuarios tengan como destino los [hologramas](../../discover/hologram.md) que crea la aplicación en [realidad mixta](../../discover/mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementación del encabezado de mira

Conceptualmente, el [encabezado](../../design/gaze-and-commit.md) se implementa mediante la proyección de un rayo desde el encabezado del usuario donde se encuentra el casco, en la dirección hacia delante hacia delante y con la determinación de la colisión del rayo.
En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md)principal de Unity, concretamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La llamada a [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado una estructura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto 3D en el que se produjo la colisión y el otro GameObject el rayo de la punta con el que está en conflicto.

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

Aunque en el ejemplo anterior se muestra cómo hacer un único Raycast en un bucle de actualización para buscar el destino al que apunta el encabezado del usuario, se recomienda hacer esto en un solo objeto que administre el encabezado en lugar de hacerlo en cualquier objeto que pueda estar interesado en el objeto que se mira. Esto permite que la aplicación guarde el procesamiento realizando una sola mirada Raycast cada fotograma.

## <a name="visualizing-head-gaze"></a>Visualización del encabezado

Al igual que en el escritorio, donde se usa un puntero del mouse para destinar e interactuar con el contenido, debe implementar un [cursor](../../design/cursors.md) que represente el encabezado del usuario. Esto proporciona a los usuarios confianza en lo que están a punto de interactuar.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Mira al principio en el kit de herramientas de realidad mixta V2
Puede obtener acceso a la parte principal del [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK V2.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Gestos y controladores de movimiento](gestures-and-motion-controllers-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Cámara](camera-in-unity.md)
* [Cursores](../../design/cursors.md)
* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
