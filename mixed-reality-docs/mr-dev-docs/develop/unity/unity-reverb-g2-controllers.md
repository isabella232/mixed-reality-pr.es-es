---
title: Controladores de HP reverberación G2 en Unity
description: Instrucciones sobre el uso de los controladores de HP reverberación G2 en SteamVR y Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberación, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638392"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controladores de HP reverberación G2 en Unity

## <a name="getting-started"></a>Introducción

No es necesario realizar ninguna configuración adicional para usar el controlador de HP reverberación G2 si está desarrollando para SteamVR o mediante la API de entrada de Windows Mixed Reality (XR. WSA. Entrada). Sin embargo, los botones A, B, X, y y el desencadenador de apriete no son accesibles actualmente a través del administrador de entrada a menos que esté usando SteamVR. La compatibilidad con las entradas de la reverberación G2 adicional estará disponible en un futuro próximo, así que asegúrese de volver a consultar.

## <a name="porting-existing-applications"></a>Trasladar aplicaciones existentes

Si ya tiene una aplicación existente que está desarrollando para los auriculares con un solo casco con Windows Mixed Reality, consulte nuestra [Guía de migración](../porting-apps/porting-guides.md) y las secciones de configuración del [proyecto](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) para obtener sugerencias generales.

## <a name="mapping-input"></a>Entrada de asignación

Cuando esté listo para poner en marcha la asignación de entrada para los nuevos controladores, comience en la sección [asignación de entrada](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) de la guía de portabilidad envolvente. Las instrucciones sobre cómo configurar entradas en Unity se detallan en [gestos y controladores de movimiento](gestures-and-motion-controllers-in-unity.md), junto con un [botón completo y una tabla de asignación de ejes](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) como referencia.

## <a name="see-also"></a>Consulte también
* [Actualización para SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)