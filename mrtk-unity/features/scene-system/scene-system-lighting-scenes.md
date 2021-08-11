---
title: Escenas de iluminación del sistema de escenas
description: Documentación sobre la iluminación en la escena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202573"
---
# <a name="lighting-scene-operations"></a>Operaciones de escena de iluminación

La escena de iluminación predeterminada definida en el perfil se carga al iniciarse. Esa escena de iluminación permanece cargada hasta `SetLightingScene` que se llama a .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Transiciones de configuración de iluminación

`transitionType` controla el estilo de la transición a una nueva escena de iluminación.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Los estilos disponibles son:

Tipo | Descripción | Duration
--- | --- | ---
Ninguno | Se descarga la escena de iluminación anterior, se carga una nueva escena de iluminación. Sin transición. | Omitido
Fadetoblack | La escena de iluminación anterior se atenua a negro. Se carga una nueva escena de iluminación y, a continuación, se desvanece de negro. Resulta útil para realizar transiciones fluidas entre ubicaciones. | Utilizado
Crossfade | La escena de iluminación anterior se atenua a medida que se desvanece la nueva escena de iluminación. Resulta útil para realizar transiciones fluidas entre las configuraciones de iluminación en la misma ubicación. | Utilizado

Tenga en cuenta que algunas configuraciones de iluminación no se pueden interpolar durante las transiciones. Si desea una transición visual fluida, esta configuración tendrá que mantener la coherencia entre escenas de iluminación.

Setting | Transición Smooth FadeToBlack | Transición smooth crossfade
--- | --- | ---
Skybox | No | No
Reflexión personalizada | No | No
Sombras en tiempo real de luz solar | Sí | No
