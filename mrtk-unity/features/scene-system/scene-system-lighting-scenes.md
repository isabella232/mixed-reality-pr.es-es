---
title: Escenas de iluminación del sistema de escenas
description: Documentación sobre la iluminación en la escena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144417"
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
Crossfade | La escena de iluminación anterior se desvanece a medida que se desvanece la nueva escena de iluminación. Resulta útil para realizar transiciones fluidas entre las configuraciones de iluminación en la misma ubicación. | Utilizado

Tenga en cuenta que algunas configuraciones de iluminación no se pueden interpolar durante las transiciones. Si desea una transición visual fluida, esta configuración tendrá que mantener la coherencia entre escenas de iluminación.

Configuración | Transición Smooth FadeToBlack | Transición smooth crossfade
--- | --- | ---
Skybox | No | No
Reflexión personalizada | No | No
Sombras en tiempo real de luz solar | Sí | No
