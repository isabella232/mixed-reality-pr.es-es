---
title: Herramienta de uso de las características de entrada
description: Herramienta InputFeatureUsage de documentación en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145011"
---
# <a name="inputfeatureusage-tool"></a>Herramienta InputFeatureUsage

La herramienta InputFeatureUsage es una herramienta en tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente la entrada de Unity disponibleFeatureUsages para un origen de entrada detectado (por ejemplo, controlador de movimiento o mano articulada).

> [!NOTE]
> Esta escena solo funciona en Unity 2019.3 o posterior.

Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware. También puede ayudar a confirmar un problema sospechoso de asignación de controles en la clase de soporte técnico para un controlador existente.

![Herramienta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso de la herramienta InputFeatureUsage

Para empezar a trabajar con la herramienta InputFeatureUsage, vaya a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** y abra la **escena InputFeatureUsageTool.** Una vez cargada la escena, el proyecto se puede ejecutar en el editor, mediante el modo de reproducción, o bien se puede crear y ejecutar en un dispositivo.

Para examinar las asignaciones de Unity para un controlador:

- Conexión del controlador
- Presione cada botón y mueva cada eje.
- Tenga en cuenta los usos de características en la pantalla
- Actualización de las asignaciones de controles en el proveedor de datos del sistema de entrada para el controlador

> [!NOTE]
> La herramienta InputFeatureUsage no usa componentes de Microsoft Mixed Reality Toolkit. Se comunica directamente con Unity para determinar y mostrar los usos de características.

### <a name="panels"></a>Paneles

Los paneles muestran el estado actual de todos los inputFeatureUsages notificados en todos los orígenes de entrada de Unity detectados.

En el panel más pequeño de la parte superior se enumeran los nombres de todos los orígenes detectados.

## <a name="see-also"></a>Consulte también

- [Creación de un proveedor de datos del sistema de entrada](../input/create-data-provider.md)
- [Herramienta de asignación de controladores](controller-mapping-tool.md)
