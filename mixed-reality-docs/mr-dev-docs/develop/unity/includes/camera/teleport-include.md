---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636375"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK proporciona un [sistema de teletransportar](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) que funciona automáticamente a través de manos y controladores articulados.

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportabilidad de MRTK.
Si decide no usar MRTK, Unity proporciona una implementación de teletraslado en el kit de [herramientas de interacción de XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Si decide implementar el suyo propio, es conveniente tener en cuenta que no puede trasladar la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de los cabezales, deberá asignar a la cámara un elemento primario en la jerarquía y, en su lugar, pasarlo a GameObject. Es el equivalente de Playspace de MRTK.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Se recomienda usar la implementación de teleportabilidad de MRTK.
Si decide implementar el suyo propio, es conveniente tener en cuenta que no puede trasladar la cámara directamente. Debido al control de Unity de la cámara para el seguimiento de los cabezales, deberá asignar a la cámara un elemento primario en la jerarquía y, en su lugar, pasarlo a GameObject. Es el equivalente de Playspace de MRTK.