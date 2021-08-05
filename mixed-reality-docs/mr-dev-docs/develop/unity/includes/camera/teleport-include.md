---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212339"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK proporciona un sistema de [teleportador](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) integrado que funciona automáticamente entre manos y controladores articulados.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportación de MRTK.
Si decide no usar MRTK, Unity proporciona una implementación de teleportación en el cuadro de [Toolkit XR.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar. Este es el equivalente del espacio de reproducción de MRTK.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportación de MRTK.
Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar. Este es el equivalente del espacio de reproducción de MRTK.