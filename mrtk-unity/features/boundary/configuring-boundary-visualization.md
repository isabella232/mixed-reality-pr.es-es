---
title: Configuración de la visualización de límites
description: Detalles para configurar el sistema de límites en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema de límites,
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177094"
---
# <a name="configuring-boundary-visualization"></a>Configuración de la visualización de límites

El *perfil de visualización de límites* proporciona opciones para configurar la apariencia visual y otros parámetros relacionados para el sistema de límites. Las visualizaciones de límites se adjuntan al Mixed Reality objeto Playspace de la escena y se teletransporta con el usuario.

## <a name="general-settings"></a>Configuración general

![Visualización general de límites Configuración](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Alto del límite

El alto del límite indica la distancia por encima del plano de suelo en el que se debe representar el límite superior. El valor predeterminado es 3 metros.

## <a name="floor-settings"></a>Configuración de la planta

![Zona de visualización de límites Configuración](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Mostrar**

Indica si se va a crear o no un plano de suelo y agregarlo a la escena. El valor predeterminado es true.

**Material**

Indica el material que se debe usar al crear el plano de suelo.

**Escala**

Indica el tamaño, en metros, del plano de suelo que se va a crear. La escala predeterminada es un cuadrado de 3 x 3 metros.

**Capa física**

Capa en la que se debe establecer el plano de suelo. El valor predeterminado es la *capa* Predeterminada.

## <a name="play-area-settings"></a>Configuración del área de reproducción

![Área de reproducción de visualización de límites Configuración](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Mostrar**

Indica si se crea o no un rectángulo de área de reproducción y se agrega a la escena. El valor predeterminado es true.

**Material**

Indica el material que se debe usar al crear el objeto de área de reproducción.

**Capa física**

Capa en la que se debe establecer el área de juego. El valor predeterminado es la *capa Omitir raycast.*

## <a name="tracked-area-settings"></a>Configuración del área de seguimiento

![Área de seguimiento de visualización de límites Configuración](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Mostrar**

Indica si se crea o no el contorno del área de seguimiento y se agrega a la escena. El valor predeterminado es true.

**Material**

Indica el material que se debe usar al crear el contorno del área de seguimiento.

**Capa física**

Capa en la que se debe establecer el área de seguimiento. El valor predeterminado es la *capa Omitir raycast.*

## <a name="boundary-wall-settings"></a>Configuración de la pared de límites

![Límites de la visualización de límites Configuración](../images/boundary/BoundaryVisualizationWallSettings.png)

**Mostrar**

Indica si los planos de la pared de límites se van a crear y agregar a la escena. El valor predeterminado es false.

**Material**

Indica el material que se debe usar al crear los planos de la pared de límites.

**Capa física**

Capa en la que se deben establecer las paredes de límite. El valor predeterminado es la *capa Omitir raycast.*

> [!NOTE]
> Establecer el componente de la pared de límites en una capa física que no sea *Ignore Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.

## <a name="boundary-ceiling-settings"></a>Configuración del límite superior

![Límite de límites de visualización de límites Configuración](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Mostrar**

Indica si se va a crear o no un plano de límite superior y agregarlo a la escena. El valor predeterminado es false.

**Material**

Indica el material que se debe usar al crear el plano de límite superior.

**Capa física**

Capa en la que se deben establecer las paredes de límite. El valor predeterminado es la *capa Omitir raycast.*

> [!NOTE]
> Establecer el componente de límite superior en una capa física que no sea *Ignore Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.

## <a name="see-also"></a>Consulte también

- [Documentación de la API de límites](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Sistema  de límites](boundary-system-getting-started.md)
