---
title: Marco de trabajo y tiempo de ejecución
description: Información relacionada con el marco de trabajo y el entorno de ejecución en MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121613"
---
# <a name="framework-and-runtime"></a>Marco de trabajo y tiempo de ejecución

## <a name="changes-to-the-scene"></a>Cambios en la escena

Para usar el kit de herramientas, una instancia del script MixedRealityToolkit debe estar en la escena.
Para agregar uno, use la opción de menú: Mixed Reality Toolkit -> Agregar a la escena y configurar. Esta instancia es responsable de registrar, actualizar y destruir servicios. También es donde se elige el perfil de configuración.

Además de agregar el GameObject de MRTK a la escena, la opción de menú también hará lo siguiente:

- Agregue MixedRealityPlayspace, que usan muchos otros componentes de MRTK para razonar sobre las transformaciones de espacio mundial y local.
- Mueva la cámara principal como elemento secundario de MixedRealityPlayspace (y agregue también algunos scripts relacionados con la entrada y la mirada a la cámara principal, lo que ayuda a encender UnityUI y a la funcionalidad de entrada relacionada con la mirada).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Objeto y tiempo de ejecución de MixedRealityToolkit

MRTK tiene varios servicios principales. Algunas se coordinan entre sí; otros son independientes.
Todos comparten el mismo ciclo de vida (inicio, registro, actualización y desmontaje), y este ciclo de vida se diferencia del ciclo de vida monobehaviour de Unity. En [esta publicación mediana](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) se explican algunos de los antecedentes y la motivación que hay detrás de este enfoque. MRTK tiene un único objeto que administra la vida y el tiempo de ejecución de sus servicios.

Esta entidad garantiza que:

- cuando se inicia el juego, la detección y la inicialización de servicios se produce en un orden predefinido.
- proporciona un mecanismo para que los servicios se registren ellos mismos (es decir, "soporte este servicio") y para que otros llamadores obtengan una retención de esos servicios.
- proporciona las llamadas Update()/LateUpdate() y las reenvía a los distintos servicios (es decir, a través de UpdateAllServices/LateUpdateAllServices).
