---
title: Contenido de la escena de Mixed Reality
description: Documentación sobre el componente de Mixed Reality de contenido de la escena
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193236"
---
# <a name="mixed-reality-scene-content"></a>Contenido de la escena de Mixed Reality

Al agregar MRTK a una escena, se `MixedRealitySceneContent` crea un gameobject. Este objeto actúa como un lugar dedicado para colocar y crear instancias Mixed Reality contenido para asegurarse de que se escala correctamente en muchas experiencias diferentes. El objeto gameobject tiene un monobehavior **MixedRealitySceneContent** equivalente, que se puede configurar mediante el parámetro **Alignment Type.** Este parámetro puede tomar los siguientes valores.

* *AlignWithExperienceScale:* alinea el contenido  en función  de la escala de la experiencia de destino y el desplazamiento del contenido establecidos en el cuadro de diálogo Experiencia del [perfil de configuración Configuración](experience-settings.md)
* *AlignWithHeadHeight:* alinea el contenido con la posición y de la cabeza del usuario, que es la ubicación de la cámara principal.


  ![Mixed Reality objeto de contenido de escena creado en el editor](../images/experience-settings/MixedRealitySceneContent.png)
