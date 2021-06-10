---
title: SceneContent
description: Documentación sobre el componente de Mixed Reality scene content
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647917"
---
# <a name="mixed-reality-scene-content"></a>Mixed Reality de escena

Al agregar MRTK a una escena, se `MixedRealitySceneContent` crea un objeto gameobject. Este objeto sirve como un lugar dedicado para colocar y crear instancias Mixed Reality contenido para asegurarse de que se escala correctamente en muchas experiencias diferentes. El objeto gameobject tiene un monobehavior **MixedRealitySceneContent** equivalente, que se puede configurar mediante el **parámetro Alignment Type.** Este parámetro puede tomar los siguientes valores.

* *AlignWithExperienceScale:* alinea el contenido  en función  de la escala de la experiencia de destino y el ajuste de contenido establecidos en la configuración de la experiencia del perfil [de configuración.](experience-settings.md)
* *AlignWithHeadHeight:* alinea el contenido con la posición y de la cabeza del usuario, que es la ubicación de la cámara principal.


  ![Mixed Reality objeto de contenido de escena creado en el editor](../images/experience-settings/MixedRealitySceneContent.png)