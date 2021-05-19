---
title: Hand Physics Extension Service
description: descripción Servicios de extensión física de mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143434"
---
# <a name="hand-physics-extension-services"></a>Servicios de extensión de física de mano

El servicio de física de manos permite eventos de colisión corporal rígida e interacciones con manos articuladas.

## <a name="getting-started-with-hand-physics-extension-service"></a>Introducción al servicio de extensión física manual

Agregue el servicio físico de mano a la lista de servicios de extensión y use el perfil predeterminado.

Una vez habilitada, use la propiedad IsTrigger de cualquier colisionador para recibir eventos de colisión de los 10 dígitos (y desconcertar si están habilitados).

### <a name="prerequisites"></a>Requisitos previos

- Se ha habilitado el servicio de extensión.
- Asigne un objeto prefab adecuado a la unión de dedo/mano.

## <a name="recommendations"></a>Recomendaciones

Aunque el servicio tiene como valor predeterminado la capa "predeterminada", se recomienda usar una capa independiente para los objetos HandPhysics. De lo contrario, puede haber colisiones no deseadas o raycasts inexactos.
