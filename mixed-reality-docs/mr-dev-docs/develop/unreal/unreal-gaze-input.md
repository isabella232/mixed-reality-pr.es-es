---
title: Mira fijamente inrealmente
description: Tutorial sobre la configuración de la entrada de fijamente para HoloLens y el motor no real
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679054"
---
# <a name="gaze-input"></a>Entrada de mira

## <a name="overview"></a>Información general

El [complemento de Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) no proporciona funciones integradas para la entrada de mirada, pero HoloLens 2 admite el seguimiento ocular. Las características de seguimiento reales son proporcionadas por las API de seguimiento de visualización y **seguimiento** de los **cabezales** y incluyen:

- Información del dispositivo
- Sensores de seguimiento
- Orientación y posición
- Recorte de paneles
- Mira la información de datos y seguimiento

Puede encontrar una lista completa de las características en la documentación de la pantalla y el [seguimiento](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) de los ojos [montados](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .

Además de las API no reales, consulte la documentación sobre la [interacción basada en miras](../../design/eye-gaze-interaction.md) en la vista de hololens 2 y lea cómo funciona el [seguimiento ocular en hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .

> [!IMPORTANT]
> El seguimiento ocular solo se admite en HoloLens 2.

## <a name="enabling-eye-tracking"></a>Habilitación del seguimiento ocular
La entrada de mirada debe estar habilitada en la configuración del proyecto de HoloLens antes de poder usar cualquiera de las API de inreal. Cuando se inicie la aplicación, verá una solicitud de consentimiento que se muestra en la captura de pantalla siguiente.

- Seleccione **sí** para establecer el permiso y obtener acceso a la entrada de mira. Si necesita cambiar esta configuración en cualquier momento, se puede encontrar en la aplicación de **configuración** .

![Permisos de entrada ocular](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos en lugar de los dos rayos necesarios para el seguimiento de Stereoscopic, que no se admite.

Esta es toda la configuración que necesitará para empezar a agregar entradas de fijamente a las aplicaciones de HoloLens 2 en el mismo equipo. Puede encontrar más información sobre la entrada y cómo afecta a los usuarios de realidad mixta en los vínculos siguientes. Asegúrese de pensar en ellos al compilar experiencias interactivas.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación: 

> [!div class="nextstepaction"]
> [Seguimiento de las manos](unreal-hand-tracking.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Calibración](../../calibration.md)
* [Comodidad](../../design/comfort.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)
