---
title: Mixed Reality contenido de la escena
description: Documentación sobre el componente de Mixed Reality scene content
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177338"
---
# <a name="mixed-reality-scene-content"></a>Mixed Reality contenido de la escena

Al agregar MRTK a una escena, se `MixedRealitySceneContent` crea un objeto gameobject. Este objeto sirve como un lugar dedicado para colocar y crear instancias Mixed Reality contenido para asegurarse de que se escala correctamente en muchas experiencias diferentes. El objeto gameobject tiene un monobehavior **MixedRealitySceneContent** equivalente, que se puede configurar mediante el **parámetro Alignment Type.** Este parámetro puede tomar los siguientes valores.

* *AlignWithExperienceScale:* alinea el contenido  en función  de la escala de la experiencia de destino y el ajuste de [contenido](experience-settings.md) establecidos en la configuración del perfil de Configuración
* *AlignWithHeadHeight:* alinea el contenido con la posición y de la cabeza del usuario, que es la ubicación de la cámara principal.


  ![Mixed Reality objeto de contenido de escena creado en el editor](../images/experience-settings/MixedRealitySceneContent.png)
