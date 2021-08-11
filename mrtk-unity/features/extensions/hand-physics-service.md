---
title: Servicio de la física de la mano
description: documentación para usar el servicio de extensión hand-physics en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221731"
---
# <a name="hand-physics-service"></a>Servicio de la física de la mano

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

El servicio de física de manos permite eventos de colisión corporal rígida e interacciones con manos articuladas.

## <a name="enabling-the-extension"></a>Habilitación de la extensión

Para habilitar la extensión, abra el perfil registeredServiceProvider. Haga `Register a new Service Provider` clic para agregar una nueva configuración. En el campo tipo de componente, seleccione HandPhysicsService. En el campo Perfil de configuración, seleccione el perfil físico de mano predeterminado incluido con la extensión.

## <a name="profile-options"></a>Opciones de perfil

### <a name="hand-physics-layer"></a>Capa de física de manos

Controla la capa a la que irán las uniones de mano con instancias.

Aunque el servicio tiene como valor predeterminado la capa "predeterminada" (0), se recomienda usar una capa independiente para los objetos físicos de mano. De lo contrario, puede haber colisiones no deseadas o raycasts inexactos.

### <a name="finger-tip-kinematic-body-prefab"></a>Prefab del cuerpo kinemático de la punta de los dedos

Controla qué prefab se crea una instancia al dedo. Para que el servicio funcione según lo previsto, el objeto prefab requiere:

- Un componente rigidbody, con isKinematic habilitado
- Colisionador
- Componente de `JointKinematicBody`

### <a name="use-palm-kinematic-body"></a>Uso del cuerpo kinemático de la mano

Controla si el servicio intentará crear una instancia de un prefab en la unión de la mano.

### <a name="palm-kinematic-body-prefab"></a>Prefab del cuerpo kinémático de la mano

Cuando `UsePalmKinematicBody` está habilitado, este es el prefab al que se va a crear una instancia. Al igual `FingerTipKinematicBodyPrefab` que , este prefab requiere:

- Un componente rigidbody, con isKinematic habilitado
- Colisionador
- Componente de `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Uso del servicio

Una vez habilitada, use la propiedad de cualquier colisionador para recibir eventos de colisión de los 10 dígitos (y descime si `IsTrigger` están habilitados).
