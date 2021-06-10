---
title: ExperienceSettings
description: Documentación sobre las distintas configuraciones de experiencia para MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647895"
---
# <a name="experience-settings"></a>Configuración de la experiencia

Uno de los desafíos de la creación de la interfaz de usuario Mixed Reality es la alineación entre distintas experiencias. Con MRTK, puede establecer y para la escena, configurará lo siguiente para que se comporte correctamente `Target Experience Scale` para la escala de `Content Offset` destino.

- Mixed Reality de escena
- Sistema de límites

  ![Configuración de la experiencia en el perfil de configuración de MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Escala de experiencia de destino

La **escala de experiencia** de destino especifica el entorno para el que se ha diseñado la experiencia. Puede tomar los siguientes valores.

* *OrientationOnly:* una experiencia que utiliza solo la orientación del casco y está alineada con la gravedad. El origen del sistema de coordenadas está en el nivel principal.
* *Sentado:* una experiencia diseñada para su uso sentado. El origen del sistema de coordenadas está en el nivel de planta.
* *De* pie: una experiencia diseñada para un uso estacionario. El origen del sistema de coordenadas está en el nivel de planta.
* *Room:* una experiencia diseñada para admitir el movimiento por una sala. El origen del sistema de coordenadas está en el nivel de planta.
* *Mundo:* una experiencia diseñada para usar y desplazarse por el mundo físico. El origen del sistema de coordenadas está en el nivel principal.

## <a name="content-offset"></a>Desplazamiento de contenido

Este parámetro especifica el alto por encima del suelo para desplazarse por el [Mixed Reality de](scene-content.md) la escena cuando **tipo** de alineación se establece en Alinear con escala **de experiencia**