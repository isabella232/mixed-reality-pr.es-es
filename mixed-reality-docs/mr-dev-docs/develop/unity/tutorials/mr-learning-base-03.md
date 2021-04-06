---
title: 'Tutoriales de introducción: 3. Configuración de los perfiles de MRTK'
description: En este curso se muestra cómo configurar los perfiles Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, spatial awareness
ms.localizationpriority: high
ms.openlocfilehash: 3b44ba6c4eac3cf7b42d15c8fb19d42676b10a4a
ms.sourcegitcommit: 5017f309827c1d20df4ce656d105a1a49ba7942c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106011144"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configuración de los perfiles de MRTK

## <a name="overview"></a>Introducción

En este tutorial, aprenderá a personalizar y configurar los perfiles de MRTK.

Los <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">perfiles de MRTK</a> constituyen un árbol de perfiles anidados que componen la información de configuración sobre cómo se deben inicializar los sistemas y las características de MRTK. El perfil de nivel superior, el perfil Configuration (Configuración), contiene perfiles anidados para cada uno de los sistemas básicos principales. Cada perfil anidado está diseñado para configurar el comportamiento de su sistema correspondiente.

En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial. Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.

Como lo visto al implementar el proyecto en HoloLens 2 durante el [tutorial anterior](mr-learning-base-02.md#congratulations), la malla <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> es una colección de mallas que representan la geometría del entorno. Es una visualización útil para ver inicialmente, pero normalmente está desactivada para evitar la distracción visual y el impacto adicional en el rendimiento al tenerla activada.

## <a name="objectives"></a>Objetivos

* Obtener información sobre cómo personalizar y configurar los perfiles de MRTK
* Ocultar la malla de reconocimiento espacial

## <a name="changing-the-spatial-awareness-display-option"></a>Cambio de la opción de visualización del reconocimiento espacial

Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:

1. Clonar el perfil de configuración predeterminado
2. Habilitar el sistema de reconocimiento espacial.
3. Clonar el perfil del sistema de reconocimiento espacial predeterminado.
4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.
5. Cambiar la visibilidad de la malla de reconocimiento espacial.

> [!NOTE]
> De forma predeterminada, los perfiles de MRTK no son editables. Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse. Hay varias capas anidadas de perfiles. Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a clonar, personalizar y configurar los perfiles de MRTK y sus opciones.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 4. Posicionamiento de los objetos en la escena](mr-learning-base-04.md)