---
title: InputFeatureUsageTool
description: Herramienta InputFeatureUsage de documentación de MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300209"
---
# <a name="inputfeatureusage-tool"></a>Herramienta InputFeatureUsage

La herramienta InputFeatureUsage es una herramienta de tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente el InputFeatureUsages de Unity disponible para un origen de entrada detectado (por ejemplo, un controlador de movimiento o una mano articulada).

> [!NOTE]
> Esta escena solo funciona en Unity 2019,3 o posterior.

Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware. También puede ayudar a confirmar un problema de asignación de control sospechoso en la clase de soporte de un controlador existente.

![Herramienta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Uso de la herramienta InputFeatureUsage

Para empezar a trabajar con la herramienta InputFeatureUsage, vaya a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** y abra la escena **InputFeatureUsageTool** . Una vez cargada la escena, el proyecto puede ejecutarse en el editor, usar el modo de reproducción o compilarse y ejecutarse en un dispositivo.

Para examinar las asignaciones de Unity para un controlador:

- Conectar el controlador
- Presione cada botón y mueva cada eje
- Tenga en cuenta los usos de las características en la pantalla
- Actualizar las asignaciones de control en el proveedor de datos del sistema de entrada para el controlador

> [!NOTE]
> La herramienta InputFeatureUsage no hace uso de los componentes del kit de herramientas de la realidad mixta de Microsoft. Se comunica directamente con Unity para determinar y mostrar los usos de las características.

### <a name="panels"></a>Paneles

Los paneles muestran el estado actual de todos los InputFeatureUsages indicados en todos los orígenes de entrada de Unity detectados.

El panel más pequeño de la parte superior muestra los nombres de todos los orígenes detectados.

## <a name="see-also"></a>Consulte también

- [Crear un proveedor de datos del sistema de entrada](../input/create-data-provider.md)
- [Herramienta de asignación de controladores](controller-mapping-tool.md)
