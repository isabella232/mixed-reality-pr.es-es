---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748527"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK proporciona un sistema de [teleportador](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) integrado que funciona automáticamente entre manos y controladores articulados.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportación de MRTK.
Si decide no usar MRTK, Unity proporciona una implementación de teleportación en [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar. Este es el equivalente del espacio de juego de MRTK.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportación de MRTK.
Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar. Este es el equivalente del espacio de juego de MRTK.