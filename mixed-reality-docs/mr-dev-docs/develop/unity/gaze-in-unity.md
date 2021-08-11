---
title: Mirada en Unity
description: Obtenga información sobre cómo usar la entrada de mirada como una forma principal para que los usuarios puedan dirigirse a los hologramas que la aplicación crea en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: mirada con los ojos, mirada con la cabeza, unity, holograma, realidad mixta, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c6a435e958a92adeed6cd965bebd0b8829e00da735bd193ca72a68acb9e0d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200123"
---
# <a name="head-gaze-in-unity"></a>Mirada con la cabeza en Unity

[La](../../design/gaze-and-commit.md) mirada es la manera principal para que los usuarios se [descumenten los hologramas](../../discover/hologram.md) que la [aplicación crea Mixed Reality](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Implementación de la mirada con la cabeza

Conceptualmente, puede determinar la [mirada](../../design/gaze-and-commit.md) con la cabeza proyectando un rayo hacia delante desde el casco del usuario para ver lo que alcanza. En Unity, la posición y la dirección de la cabeza del usuario se exponen a través de [la cámara](camera-in-unity.md), específicamente [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Llamar [a Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) proporciona un [Objeto RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto de colisión 3D y el otro GameObject al que se ha alcanzado el rayo de mirada con la cabeza.

### <a name="example-implement-head-gaze"></a>Ejemplo: Implementación de la mirada con la cabeza

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

Aunque en el ejemplo anterior se muestra un único raycast desde el bucle de actualización para buscar el destino en el que se encuentran los puntos principales del usuario, se recomienda usar un solo objeto para administrar todos los procesos de mirada con la cabeza. La combinación de la lógica de mirada con la cabeza ahorrará la potencia de procesamiento valiosa de la aplicación y limitará la difusión por rayos a uno por fotograma.

## <a name="visualizing-head-gaze"></a>Visualización de la mirada con la cabeza

Al igual que con un puntero del mouse en un equipo, debe implementar un [cursor](../../design/cursors.md) que represente la mirada con la cabeza del usuario. Saber qué contenido tiene como destino un usuario aumenta la confianza en lo que está a punto de interactuar.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Mirada con la cabeza en el Mixed Reality Toolkit

Puede acceder a la mirada con la cabeza desde [el Administrador de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview) en MRTK.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra en medio de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

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