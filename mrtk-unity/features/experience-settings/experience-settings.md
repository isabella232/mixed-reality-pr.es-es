---
title: Configuración de la experiencia
description: Documentación sobre las distintas configuraciones de experiencia para MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177352"
---
# <a name="experience-settings"></a>Configuración de la experiencia

Uno de los desafíos de la creación de la interfaz de usuario Mixed Reality es la alineación entre distintas experiencias. Con MRTK, puede establecer y para la escena, configurará lo siguiente para que se comporte correctamente `Target Experience Scale` para la escala de `Content Offset` destino.

- Mixed Reality de escena
- Sistema de límites

  ![Experiencia Configuración en el perfil de configuración de MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Escala de experiencia de destino

La **escala de experiencia de** destino especifica el entorno para el que se ha diseñado la experiencia. Puede tomar los siguientes valores.

* *OrientationOnly:* una experiencia que utiliza solo la orientación del casco y está alineada por gravedad. El origen del sistema de coordenadas está en el nivel principal.
* *Asentado:* una experiencia diseñada para su uso asentado. El origen del sistema de coordenadas está en el nivel de planta.
* *De* pie: una experiencia diseñada para un uso permanente de forma permanente. El origen del sistema de coordenadas está en el nivel de planta.
* *Room:* una experiencia diseñada para admitir el movimiento en una sala. El origen del sistema de coordenadas está en el nivel de planta.
* *Mundo:* una experiencia diseñada para usar y desplazarse por el mundo físico. El origen del sistema de coordenadas está en el nivel principal.

## <a name="content-offset"></a>Desplazamiento de contenido

Este parámetro especifica el alto por encima del suelo para desplazarse por el [Mixed Reality de](scene-content.md) la escena cuando **tipo** de alineación está establecido en Alinear con escala **de experiencia**
